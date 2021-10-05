## C++ Final Project - Getting Started

Below is a simple outline of how you might read in an image, process the pixel values using Process 1, and write the result out to a new image file. If you follow the outline below, you should be able to get the basic framework for processing your first image using Process 1\. From there, you are going to have to add the additional process functions and build out the menu system (user interface), but this should at least help you get started.  

_Hint: If you read the Project Description again carefully, you will notice that in the Data Structure, Read/Write Functions, and Image Processing Functions sections all of the code needed to implement the outline below is already given to you in bits and pieces._  


		vector<vector<Pixel>> process_1(const vector<vector<Pixel>>& image)
		{
			// Get the number of rows/columns from the input 2D vector (remember: num_rows is height, num_columns is width)

			// Define a new 2D vector the same size as the input 2D vector

			// For each of the rows in the input 2D vector

				// For each of the columns in the input 2D vector

					// Get the color values for the pixel located at this row and column in the input 2D vector

					// Perform the operation on the color values (refer to Runestone for this)

					// Save the new color values to the corresponding pixel located at this row and column in the new 2D vector

			// Return the new 2D vector after the nested for loop is complete
		}

		int main()
		{
			// Read in BMP image file into a 2D vector (using read_image function)

			// Call process_1 function using the input 2D vector and save the result returned to a new 2D vector

			// Write the resulting 2D vector to a new BMP image file (using write_image function)
		}
