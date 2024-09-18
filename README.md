# LEETCODE-Array-179
Let's perform a dry run of the `largestNumber` function for a specific input. Suppose the input array is:

```java
int[] nums = {3, 30, 34, 5, 9};
```

### Code Explanation:

1. **Step 1: Convert `nums` array into an Integer array**:
   - The `nums` array `{3, 30, 34, 5, 9}` is converted to an `Integer[]` array.
   - The `Arrays.stream(nums).boxed().toArray(Integer[]::new)` converts each element of the `int[] nums` array into its boxed `Integer` counterpart.

   So after this step, `x` becomes:

   ```java
   Integer[] x = {3, 30, 34, 5, 9};
   ```

2. **Step 2: Custom Sorting**:
   - The array `x` is sorted based on a custom comparator defined as `(a, b) -> (s2 + s1).compareTo(s1 + s2)`.
   - The goal of this sorting is to ensure that when two numbers are concatenated, the larger combination is placed first.

   - For `a = 3` and `b = 30`, the comparator will compare:
     - `"303"` (`s1 = "3", s2 = "30"`)
     - `"330"` (`s1 = "30", s2 = "3"`)
     - Since `"330"` > `"303"`, `30` should come after `3`.
     
   - For `a = 9` and `b = 34`, the comparator will compare:
     - `"934"` and `"349"`
     - Since `"934"` > `"349"`, `9` should come before `34`.

   Sorting the array based on this comparator results in:

   ```java
   Integer[] x = {9, 5, 34, 3, 30};
   ```

3. **Step 3: Handle Leading Zeros**:
   - If the largest number is `0` (i.e., `x[0] == 0`), the function returns `"0"` to prevent numbers like `"000"`.

   In this case, the first element is `9`, so this check does not trigger.

4. **Step 4: Construct the Result**:
   - We use a `StringBuilder` to concatenate the sorted numbers in order.
   
   ```java
   result = "9534330";
   ```

5. **Step 5: Return the Result**:
   - The function returns `"9534330"` as the largest possible number that can be formed by concatenating the elements of the array.

### Final Output:

The output for the input `{3, 30, 34, 5, 9}` is `"9534330"`.

### Dry Run Trace:

| Step   | `x` Array                  | Comparator Results | Final Sorted `x` | Result |
|--------|----------------------------|--------------------|------------------|--------|
| Input  | `{3, 30, 34, 5, 9}`         | Compare pairs      | `{9, 5, 34, 3, 30}` | `"9534330"` |
