# FDW_PD_ConnectAdminLink Calibration Validation Guide

## Overview

The `FDW_PD_ConnectAdminLink` function redistributes agricultural area and production data from old administrative boundaries to new ones. This guide explains the validation improvements and how to use them effectively.

## What Changed

### Previous Validation (Before)

```python
# Old validation with fixed 1% threshold
area_new, prod_new = FDW_PD_ConnectAdminLink(link_ratio, area, prod, validation=True)
```

The old validation:
- Used a fixed 1% threshold that couldn't be adjusted
- Had a flawed formula: `(area.sum(1) + 0.01)` that made validation unreliable for small values
- Provided minimal diagnostic information when validation failed
- Failed without explaining which years or by how much

### New Validation (After)

```python
# New validation with flexible threshold and diagnostics
area_new, prod_new = FDW_PD_ConnectAdminLink(
    link_ratio, area, prod,
    validation=True,
    threshold_pct=1.0,  # Configurable threshold (default: 1.0%)
    verbose=True         # Show detailed diagnostics (default: False)
)
```

The new validation:
- **Configurable threshold**: Adjust `threshold_pct` based on your data quality needs
- **Smart thresholding**: Uses absolute thresholds for very small values, relative for larger ones
- **Detailed diagnostics**: Shows which years fail and by how much
- **Informative errors**: Explains what went wrong and suggests solutions
- **Better accuracy**: Fixed formula that properly handles edge cases

## Understanding Validation Failures

### Why Do Differences Occur?

Even with perfect ratios, small discrepancies (< 1%) can occur due to:

1. **Missing Data (NaN) Handling**
   - When data is missing for some units, the `fill_value=0` in aggregation can cause imbalances
   - Ratios may not account for patterns of missing data

2. **Ratio Precision**
   - Ratios may not sum to exactly 1.0 due to floating-point rounding
   - Cropland-based ratios (CBR) may have incomplete geographic coverage
   - Data availability may differ between old and new boundaries

3. **Numerical Precision**
   - Floating-point arithmetic accumulates small errors over many operations
   - Multiple multiplications and additions compound rounding errors

### When to Adjust the Threshold

| Scenario | Recommended Threshold | Rationale |
|----------|----------------------|-----------|
| High-quality, complete data | `threshold_pct=0.5` | Expect minimal discrepancies |
| Standard production data | `threshold_pct=1.0` (default) | Balance accuracy and tolerance |
| Significant boundary changes | `threshold_pct=2.0` | More tolerance for redistribution errors |
| Sparse or incomplete data | `threshold_pct=5.0` | Account for missing data patterns |
| Exploratory analysis | `validation=False` | Skip validation entirely |

## Usage Examples

### Example 1: Standard Usage with Diagnostics

```python
# Enable verbose output to see what's happening
area_new, prod_new = FDW_PD_ConnectAdminLink(
    link_ratio, area, prod,
    validation=True,
    threshold_pct=1.0,
    verbose=True
)
```

**Output when passing:**
```
--- FDW_PD_ConnectAdminLink Validation Report ---
Threshold: 1.0% relative difference
Absolute thresholds: area=0.001 ha, prod=0.001 mt

Area validation: PASSED (max difference: 0.0234%)

Production validation: PASSED (max difference: 0.0156%)
------------------------------------------------
```

### Example 2: Handling Validation Failures

```python
# If validation fails, try increasing the threshold
try:
    area_new, prod_new = FDW_PD_ConnectAdminLink(
        link_ratio, area, prod,
        validation=True,
        threshold_pct=1.0,
        verbose=True
    )
except AssertionError as e:
    print(f"Validation failed: {e}")
    print("Trying with relaxed threshold...")
    
    area_new, prod_new = FDW_PD_ConnectAdminLink(
        link_ratio, area, prod,
        validation=True,
        threshold_pct=2.0,
        verbose=True
    )
```

**Output when failing then succeeding:**
```
--- FDW_PD_ConnectAdminLink Validation Report ---
Threshold: 1.0% relative difference
...
Area validation: 3 year(s) exceed threshold:
  Year 2015: old=1234.56 ha, new=1248.92 ha, diff=14.36 ha (1.163%)
  Year 2016: old=1345.67 ha, new=1362.34 ha, diff=16.67 ha (1.238%)
  Year 2017: old=1456.78 ha, new=1473.89 ha, diff=17.11 ha (1.175%)
...
Validation failed: Area calibration validation failed: 3 year(s) exceed 1.0% threshold...

Trying with relaxed threshold...

--- FDW_PD_ConnectAdminLink Validation Report ---
Threshold: 2.0% relative difference
...
Area validation: PASSED (max difference: 1.238%)

Production validation: PASSED (max difference: 1.156%)
------------------------------------------------
```

### Example 3: Debugging Specific Years

When validation fails, the verbose output tells you exactly which years are problematic:

```python
area_new, prod_new = FDW_PD_ConnectAdminLink(
    link_ratio, area, prod,
    validation=True,
    threshold_pct=1.0,
    verbose=True
)
```

The output shows:
- Which years exceed the threshold
- Old vs new totals for those years
- Absolute difference in ha or mt
- Percentage difference

This helps you:
1. Identify if the problem is systematic or isolated to specific years
2. Determine if the issue is with area, production, or both
3. Decide whether to adjust thresholds or investigate data quality

### Example 4: Backwards Compatibility

The changes are backwards compatible. Existing code continues to work:

```python
# Old code still works with default 1% threshold
area_new, prod_new = FDW_PD_ConnectAdminLink(link_ratio, area, prod, validation=True)

# Equivalent to:
area_new, prod_new = FDW_PD_ConnectAdminLink(
    link_ratio, area, prod,
    validation=True,
    threshold_pct=1.0,
    verbose=False
)
```

## Best Practices

1. **Start with verbose=True**: When developing or debugging pipelines, always enable verbose output to understand validation results

2. **Adjust threshold based on context**:
   - Use stricter thresholds (0.5%) for high-quality data
   - Use looser thresholds (2-5%) for data with known issues

3. **Investigate persistent failures**: If you consistently need thresholds > 5%, investigate:
   - Data quality issues
   - Ratio calculation problems
   - Missing data patterns

4. **Document threshold choices**: When using non-default thresholds, document why in your code

5. **Test with validation=True first**: Even if you plan to disable validation in production, test with it enabled during development

## Migration Checklist

For existing notebooks using `FDW_PD_ConnectAdminLink`:

- [ ] Code continues to work as-is (backwards compatible)
- [ ] Consider adding `verbose=True` for better diagnostics
- [ ] If you previously used `validation=False` due to failures:
  - [ ] Try `validation=True` with `threshold_pct=2.0` or higher
  - [ ] Use `verbose=True` to understand what threshold is appropriate
- [ ] Update any error handling to account for more informative error messages
- [ ] Document your threshold choice if using non-default values

## Technical Details

### Absolute vs Relative Thresholds

The validation uses a hybrid approach:

- **For large totals** (> 0.001 ha or mt): Use relative threshold
  - Example: 1000 ha ± 1% = 990-1010 ha acceptable
  
- **For small totals** (≤ 0.001 ha or mt): Use absolute threshold
  - Example: 0.0005 ha must match within 0.001 ha (not 1%)
  - Prevents false failures due to rounding on tiny values

### Error Message Format

When validation fails, the error message includes:

1. Number of years exceeding threshold
2. Which threshold was used
3. Worst-case year and its percentage difference
4. Suggestion to increase threshold or investigate data quality

Example:
```
AssertionError: Area calibration validation failed: 3 year(s) exceed 1.0% threshold.
Worst case: year 2015 with 1.238% difference.
Consider increasing threshold_pct or investigating data quality.
```

## Questions?

If you have questions about:
- Why your data fails validation: Use `verbose=True` to diagnose
- What threshold to use: See the scenarios table above
- How validation works: See the function docstring in `tools.py`

For additional support, please open an issue on GitHub.
