---
Date: 2025-03-21
tags:
  - Leetcode
  - java
  - data_structure
URL: https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/description/
Hint: 
Clarity: 
Solution Type: 
Hardness: 
cssclasses:
  - programming-notes
---

### Intuition
- we can store all the available supplies in a hashset, for instant access.
- and then we can just check ingredients for each recipe 
---
- we can use BFS / DFS
- or we can use [[Kahn's Algorithm]] 

> [!info] References
> - [Tech Dose -Find All Possible Recipes from Given Supplies \| Leetcode 2115 - YouTube](https://youtu.be/mQQJlknAA6A)
> - [BFS Solution - Brainrot Post](https://leetcode.com/problems/find-all-possible-recipes-from-given-supplies/solutions/6562413/bro-thinks-he-s-gordon-ramsay-cooking-recipes-with-bfs-dfs)
### Optimized Solution
```java

```
### Follow Up Solution
```java fold title="BFS Solution"
class Solution {
    public List<String> findAllRecipes
    (String[] recipes, List<List<String>> ingredients, String[] supplies) {
        
        // Store all initially available supplies in a HashSet for quick lookup
        HashSet<String> available = new HashSet<>(Arrays.asList(supplies));

        // A HashMap to store each recipe and its required ingredients
        // Key: Recipe name | Value: List of required ingredients
        HashMap<String, List<String>> book = new HashMap<>();
        for (int i = 0; i < recipes.length; i++)
            book.put(recipes[i], ingredients.get(i));

        boolean updated = true;

        // Loop until no new recipe can be made
        while (updated) {
            updated = false; // Reset update flag

            for (String recipe : recipes) {
                // If the recipe is already in 'available', skip it
                if (available.contains(recipe)) 
                    continue;

                boolean possible = true; // Flag to check if we can make the recipe

                // Check if all required ingredients are available
                for (String ingredient : book.get(recipe)) {
                    // If any ingredient is missing, recipe cannot be made
                    if (!available.contains(ingredient)) { 
                        possible = false;
                        break; // No need to check further
                    }
                }

                // If all ingredients are available, add recipe to available set
                if (possible) {
                    available.add(recipe);
                    updated = true; // Mark as updated to continue checking
                }
            }
        }

        // Collect all recipes that are possible to make
        List<String> res = new ArrayList<>();
        for (String recipe : recipes)
            if (available.contains(recipe))
                res.add(recipe);
        
        return res;
    }
}
```
### Initial Solution
```java title="❌ Naive Solution"
class Solution {
    public List<String> findAllRecipes(String[] recipes, List<List<String>> ingredients, String[] supplies) {
        List<String> res = new ArrayList<>();
        boolean possible = true;

        // for all available supplies
        HashSet<String> available = new HashSet<>();
        for (String s : supplies)
            available.add(s);

        for (int i = 0; i < recipes.length; i++) {
            for (int j = 0; j < ingredients.get(i).size(); j++) {
                if (!available.contains(ingredients.get(i).get(j))) {
                    possible = false;
                    break;
                }
            }
            if (possible){
                res.add(recipes[i]);
                available.add(recipes[i]); //  or we should just also check res list 
            }
            possible = true;
        }
        return res;
    }
}
```
### Key Takeaways
BFS Notes
- **Uses `HashSet` (`available`)** → Enables **O(1) lookup** for checking available ingredients.
- **Uses `HashMap` (`book`)** → Stores recipes and their required ingredients for easy access.
- **Uses a `while` loop with `updated` flag** →
    - Keeps running **until no new recipe is added** (handles multi-step dependencies).
    - Example: `"bread"` might be required for `"sandwich"`, so `"sandwich"` should only be possible after `"bread"` is made.
- **Checks each recipe only when necessary** →
    - **Skips already available recipes** for efficiency.
- **Breaks inner loop early (`break`)** →
    - If any ingredient is missing, **stops checking further** (saves computation).

*similar to:* 
- 