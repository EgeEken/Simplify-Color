# Simplify Color

# V4
Simplifies the colors of an image, bringing the total amount of different colors down to a desired amount. Mostly to create stylized simplistic renditions of pictures but in certain cases it allows for size compression while keeping the resolution, general shape and structure in the original image.

This program picks the given number of colors at random, so running it with the same coefficients twice will result in different images, especially so with smaller amounts of colors.

See also: [Simplify](https://github.com/EgeEken/Simplify)

Known issues:
- Only square images (with the same horizontal and vertical length) work

# Itzhak Perlman
![Github readme itzhak](https://user-images.githubusercontent.com/96302110/170580353-ad76f66e-6f5a-4bab-8a12-8bd7a17de28f.png)

In this example, the bottom result contains only 10 different colors, and as such has a significantly smaller file size than the original, while still being obviously a picture of the violinist, albeit a very stylized depiction. The result on top on the other hand, using only 100 colors, does not show a significant loss in detail for the most part. Granted, the difference is clear when paying attention but considering that the original image was using 109990 different colors, and had roughly twice the file size, I believe this is a pretty good demonstration.

# The Leaning Tower of Pisa
![Github readme pisa](https://user-images.githubusercontent.com/96302110/170580388-db096f8f-d03e-4bbf-97f5-e9a75312eef0.png)

An important aspect to note is the randomness of the created images, this allows for you to create a countless amount of different stylized simplified images from any given image, all automatically.

![Github readme pisa 10](https://user-images.githubusercontent.com/96302110/170580439-ef7c68e0-0912-4f77-b0bd-64bb522ac7e4.png)

Using the "Simplify Colors (gif)" file, you can create several images at a time, and create a gif of all the created images at the end.

# 50 results with 10 colors at 3 FPS
![giftest](https://user-images.githubusercontent.com/96302110/170581462-9515b7ab-9a21-435a-b206-d37c8517da11.gif)


# V5.1
Simplifies the colors further using a chain-clustering algorithm inspired by the k-means system I learned about in the data science class in my first semester. The algorithm finds chains of similar colors, it starts with the "first" (arbitrarily chosen by set generation) different color after placing all different colors in a 3d space represented by the RGB axes, then finds the closest color, adding it to the chain, it keeps finding the closest color until it starts going back by finding a color thats already part of the chain, or by being forcibly terminated by finding a color thats part of another chain. After creating these clusters, it finds their centers with a simple average function, then uses effectively the same system as in v4 to fit the colors in the image into the new color palette created by the center points of the clusters.

2D demonstration of how the chain system works, 10 randomly generated points in a 100x100 space formed 7 chains with the algorithm, the gray points represent the points and the stars represent the cluster centers
![demonstration github](https://user-images.githubusercontent.com/96302110/171171932-25d46832-9ab1-4e4c-8a2f-417c8393f310.png)

The program is recursive and at the end of each created image, will ask if you would like to continue, if you choose to continue after the end (where theres only 1 color, making it completely unrecognizable), it will ask for an FPS value and create a GIF of the progression towards that final image which is just a single color. 

In most cases, each iteration roughly halves the amount of different colors. (The exact value i found while testing around with the algorithm before the final result was specifically 53.3% for three dimensions, the formula being | cluster count ~= total coord count * 0.533 | , the mathematical reason behind this, I don't completely understand yet but there seems to be a universal ratio that works for every coord count in every space range regardless of the dimension count (it was 4.8 for 1 dimension))

![image](https://user-images.githubusercontent.com/96302110/170829538-a8e3a385-1379-4fc3-b3f3-a663d06afbc3.png)

Warning: The algorithm is very heavy and would take an incredibly long time with most pictures, I wouldn't recommend using it with a starting image with over 300 colors, maybe less depending on your computing power. You can use the V4 program above to simplify the picture down to a desired low number of colors, then use v5 on that new created image

![itzhaksq_v4_200_Simplified_GIF](https://user-images.githubusercontent.com/96302110/170827531-38785b7f-4ed3-4b74-b26e-5dd80c32f414.gif)

![pisa_Simplified_150 0_1_Simplified_GIF](https://user-images.githubusercontent.com/96302110/170828450-29f26b31-82b9-4185-844a-ead8cb2b536d.gif)


# V5.2
This version uses the same general system as V5.1, but uses a different clustering algorithm, [the hiearchical system](https://en.wikipedia.org/wiki/Hierarchical_clustering). This allows for faster computing of clusters, and also of specific color counts just like v4, unlike in v5.1 which chose the amount of colors based on the results of the chain cluster algorithm. However, i personally found that the results are inferior to those from v5.1.

2D Demonstration of how the chain system works:

![proper_GIF](https://user-images.githubusercontent.com/96302110/175520436-b09e5238-da8a-48e9-9240-4511b4ba24e8.gif)

# Comparisons with Octree, V5.1 and V5.2:

![comparison](https://user-images.githubusercontent.com/96302110/175521247-b28254cb-6225-4b42-83bf-6eaee473636d.png)

![comparison](https://user-images.githubusercontent.com/96302110/175521180-5cfc8346-a8fa-4d5a-9d16-885db5843376.png)


# Results of a survey comparing the three

The participants were not told which algorithm was which.

![image](https://user-images.githubusercontent.com/96302110/175522239-719d36ba-37c5-4ac8-8e25-f6d1ef07cc37.png)

# Conclusion

Overall, octree is still a more consistent algorithm, that generally brings out better results, and its significantly faster than either of my algorithms, but speaking strictly of results, it seems v5.1 puts out comparable or sometimes even better results than octree, reaching as much as 80% of the votes in one comparison where octree received only 8%. I'm quite happy with these results considering the amount of industry applications of the octree color simplification algorithm. 

The most notable difference to me seems to be octree's (and v5.2's) tendency to sacrifice contrast in favor of more a consistent image, whereas v5.1 generally tends to keep the contrast between the object and background more noticable especially at lower color counts, i believe the difference between the results for octree and v5.1 at 3 colors on the eiffel tower picture illustrate this difference the best:

![comparison 3 (wasnt included in the original picture)](https://user-images.githubusercontent.com/96302110/175523669-01cbef17-fe98-4bb2-8c3f-f09091a3b07d.png)
