# C++ Final Project - Test & Debug Functions (Optional)

You may find it difficult to test and debug your image processing functions using the sample image supplied (**if you're not having any trouble producing the correct images, you can safely ignore this page**). If your function has a problem, inspecting the resulting image may not always be helpful since you cannot tell at a pixel level what your code is doing wrong. If you attempt to instead print out each of the pixel values of the sample image using cout statements, you may be overwhelmed by sheer number of pixel values displayed and it will be hard to debug that way.  

For that reason, we recommend that you start small and initially test your image processing functions using a very tiny "image" or 2-dimensional vector with predictable values. Since our image processing functions take in a 2D vector of Pixel values, we can manufacture our own tiny 2D vector to test with (instead of reading in a large image into a large 2D vector). For example, below is one way to initialize a 2D vector of Pixel values to test with. This tiny 2D vector has 3 rows and 4 columns of Pixels (each Pixel containing red, green, blue color values):


		vector<vector<Pixel>> tiny =
			{
				{{  0,  5, 10},{ 15, 20, 25},{ 30, 35, 40},{ 45, 50, 55}},
				{{ 60, 65, 70},{ 75, 80, 85},{ 90, 95,100},{105,110,115}},
				{{120,125,130},{135,140,145},{150,155,160},{165,170,175}}
			};

Note: This is an illustration of what those pixel (red, green, blue) values or color values would look like in an image:  

![](doc_images/pixel_values.png?raw=true)

Then, we can pass that tiny 2D vector into one of the image processing functions and get the resulting 2D vector:


		vector<vector<Pixel>> result = process_1(tiny);


Finally, we can print out the resulting pixel values on the command line using cout statements:

		for (int row = 0; row < result.size(); row++)
			{
				for (int col = 0; col < result[0].size(); col++)
				{
					cout << setw(3) << result[row][col].red << " ";
					cout << setw(3) << result[row][col].green << " ";
					cout << setw(3) << result[row][col].blue << " ";
				}
				cout << endl;
			}

_Note: We are not using the read_image and write_image functions here. Instead, we are manually creating a small test 2D vector, passing that into the process functions, and then printing out the resulting 2D vector. The read_image function is used to get a 2D vector from a BMP image and the write_image function is used to get a BMP image from a 2D vector, so we are bypassing those steps here._  

* * *

In order to assist with your debugging, we are including below the expected output from running the test code using the tiny test 2D vector above for each of the image processing functions so you have something to compare to. Please note that your values may not match up exactly with the values shown below due to rounding issues or variations in implementation. However, if your function is working as expected, most of the values should be close and this will give you some confidence that you are on the right track. It will also be easier to debug your function since you know the exact pixel values going in (i.e. the values shown in the tiny test image above) and expected pixel values coming out (i.e. the values shown in the output below).  

**PROCESS 1:**

<pre>  0   0   1   5   7   9  15  17  20  17  19  21 
 18  20  21  47  50  53  75  79  83  65  69  72 
 37  39  40  84  87  90 125 129 133 103 106 109</pre>

**PROCESS 2** (with scaling_factor=0.3):

<pre>  0   1   3   4   6   7   9  10  12  13  15  16 
 18  19  21  22  24  25  90  95 100 105 110 115 
120 125 130 135 140 145 150 155 160 228 229 231</pre>

**PROCESS 3:**

<pre>  5   5   5  20  20  20  35  35  35  50  50  50 
 65  65  65  80  80  80  95  95  95 110 110 110 
125 125 125 140 140 140 155 155 155 170 170 170 </pre>

**PROCESS 4:**

<pre>120 125 130  60  65  70   0   5  10 
135 140 145  75  80  85  15  20  25 
150 155 160  90  95 100  30  35  40 
165 170 175 105 110 115  45  50  55</pre>

**PROCESS 5** (with number=2):

<pre>165 170 175 150 155 160 135 140 145 120 125 130 
105 110 115  90  95 100  75  80  85  60  65  70 
 45  50  55  30  35  40  15  20  25   0   5  10</pre>

**PROCESS 6** (with x_scale=2, y_scale=3):

<pre>  0   5  10   0   5  10  15  20  25  15  20  25  30  35  40  30  35  40  45  50  55  45  50  55 
  0   5  10   0   5  10  15  20  25  15  20  25  30  35  40  30  35  40  45  50  55  45  50  55 
  0   5  10   0   5  10  15  20  25  15  20  25  30  35  40  30  35  40  45  50  55  45  50  55 
 60  65  70  60  65  70  75  80  85  75  80  85  90  95 100  90  95 100 105 110 115 105 110 115 
 60  65  70  60  65  70  75  80  85  75  80  85  90  95 100  90  95 100 105 110 115 105 110 115 
 60  65  70  60  65  70  75  80  85  75  80  85  90  95 100  90  95 100 105 110 115 105 110 115 
120 125 130 120 125 130 135 140 145 135 140 145 150 155 160 150 155 160 165 170 175 165 170 175 
120 125 130 120 125 130 135 140 145 135 140 145 150 155 160 150 155 160 165 170 175 165 170 175 
120 125 130 120 125 130 135 140 145 135 140 145 150 155 160 150 155 160 165 170 175 165 170 175</pre>

**PROCESS 7:**

<pre>  0   0   0   0   0   0   0   0   0   0   0   0 
  0   0   0   0   0   0   0   0   0   0   0   0 
  0   0   0 255 255 255 255 255 255 255 255 255</pre>

**PROCESS 8** (with scaling_factor=0.5):

<pre>127 130 132 135 137 140 142 145 147 150 152 155 
157 160 162 165 167 170 172 175 177 180 182 185 
187 190 192 195 197 200 202 205 207 210 212 215</pre>

**PROCESS 9** (with scaling_factor=0.5):

<pre>  0   2   5   7  10  12  15  17  20  22  25  27 
 30  32  35  37  40  42  45  47  50  52  55  57 
 60  62  65  67  70  72  75  77  80  82  85  87 </pre>

**PROCESS 10:**

<pre>  0   0   0   0   0   0   0   0   0   0   0   0 
  0   0 255   0   0 255   0   0 255   0   0 255 
  0   0 255   0   0 255   0   0 255   0   0 255 </pre>

Once you're able to match the outputs above with your code, you can then test your functions using the real sample image provided (i.e. sample.bmp), along with the read and write image functions (i.e. read_image, write_image), and compare the resulting images created to the sample output images provided with the project.