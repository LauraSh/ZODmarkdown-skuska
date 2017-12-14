
# Image sharpness detection and autofocus 

## detect image sharpness -> use edges to compare sharpness of 2 images

``` matlab

A = imread('kytka256.jpg');
A = rgb2gray(A);

hsize = 50; 
sigma = 5;
f = fspecial('gaussian',hsize,sigma);

Af = imfilter(A,f);
Ae =edge(A);
Aef =edge(Af);

s = 1;
cols = 3;
rows = 2;

subplot(rows,cols,s);s=s+1;imshow(A);title('original');
subplot(rows,cols,s);s=s+1;imshow(Af);title('filtered');
subplot(rows,cols,s);s=s+1;mesh(f);title(['filtr. hsize: ' num2str(hsize),', sigma: ' num2str(sigma)]);
colormap('hot')
subplot(rows,cols,s);s=s+1;imshow(Ae);title(['edges: ', num2str(sum(Ae(:))), ' px' ]);
subplot(rows,cols,s);s=s+1;imshow(Aef);title(['edges: ', num2str(sum(Aef(:))), ' px' ]);
```
