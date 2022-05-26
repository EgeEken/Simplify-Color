# Simplify-Color
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
