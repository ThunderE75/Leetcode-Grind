---
Hardness: Easy
No.: "733"
Solution Type:
  - DFS
Que Type:
  - Array
Clarity: Low
URL: https://leetcode.com/problems/flood-fill/description/
Date: 2024-11-06T20:20
Week:
  - Week 1
Next Review: November 10, 2024
---
> Try to solve this, almost similar to it  
>   
> [https://leetcode.com/problems/number-of-islands/description/](https://leetcode.com/problems/number-of-islands/description/)

## Assisted Solution [DFS]

```Java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        // We pass everything to the recurive function as is, & also the color of the starting pixels
        paint(image, sr, sc, color, image[sr][sc]);
        return image;
    }
    // The return type is void so we can return null when we reach a dead end
    public void paint(int[][] img, int i, int j, int color, int sColor){
        
        // When dealing with index, this check should always be the 1st thing
        // Checking if the i & j are inside the bounds of the provided image[][]
        if(i < 0 || i >= img.length || j < 0 || j >= img[0].length) return ;

        // 1- We check if the color of the pixel is not same as the starting pixel color
        // 2- We check if the pixel already have the desired color
        // we skip this pixel
        if (img[i][j] != sColor || img[i][j] == color) return ;
        
        // Coloring the pixel
        img[i][j] = color;
        
        // recursivelly going to adjecent pixels
        paint(img, i+1,j,color,sColor);
        paint(img, i-1,j,color,sColor);
        paint(img, i,j+1,color,sColor);
        paint(img, i,j-1,color,sColor);
    }
}
```

> [!info] Flood Fill - LeetCode  
> Can you solve this real interview question?  
> [https://leetcode.com/problems/flood-fill/solutions/3476692/java-100-faster-full-explaination-comments-lbeginner-friendly/](https://leetcode.com/problems/flood-fill/solutions/3476692/java-100-faster-full-explaination-comments-lbeginner-friendly/)  

---

## Key Takeaways

## Video Resources

- [https://youtu.be/aehEcTEPtCs](https://youtu.be/aehEcTEPtCs)
- [https://youtu.be/VuiXOc81UDM?t=58](https://youtu.be/VuiXOc81UDM?t=58)

## Initial Attempt [Not Working]

```Java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        return paint(image, sr, sc, color, image[sr][sc]);
    }
    public static int[][] paint(int[][] img, int i, int j, int color, int sColor){
        
        if(i < img.length || i > img.length) return img;
        if(j < img[i].length || j > img[i].length) return img;

        // coloring the adjecent pixels
        paint(img, i+1,j,color,sColor);
        paint(img, i-1,j,color,sColor);
        paint(img, i,j+1,color,sColor);
        paint(img, i,j-1,color,sColor);
        
        if (img[i][j] == sColor){
            img[i][j] = color;
        }
        return img;
    }
}
```