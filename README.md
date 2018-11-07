# Detection ofunattended objects at public places using opencv
# WORKING OF PROPOSED MODEL
The system proposed here takes video as input and extracts frames of the video. It sets the first frame of the video as the background frame for the further process. Then in the pre-processing step first the image is turned into gray, then histogram equalization Is performed  on the gray image in order to increase the contrast in the image. After increasing contrast I have applied the gaussian blur method to blur the edges of objects.
Once the pre-processing is completed on both background and current frame, I have applied background subtraction with appropriate thresholding. Now I have applied morphological operation like dilation and erosion in order to fill the holes in blobs of subtracted  image. After applying morphological operation I have applied canny edge detector to find the edges in the subtracted image
Now we have initialised a circular dictionary and a counter(frameno)(Dictionary and counter will be initialised before the while loop applied ). The counter will count, no of frames passed in the input video. The circular dictionary here contain frameno as its key and a empty list as value.
Now I have detect all the blobs in the current frame using ‘findcontour()’ method. After finding the blobs ,the centroid of each blob of the current frame was appended to a list and finally the list is appended to the dictionary as the value of the corresponding frameno.
Now for each blob we have checked whether the centroid of the particular blob is available in the list of 50 frames back, 100 frames back and 190 frames back. If the the centroid is available the mentioned frames then check whether the area of blob lies in between 100 to 15000 it is true then a rectangle of red colour will be drawn on the object and text will be printed as “unattended object”. 
If the system gives any wrong prediction then press key “a” and it the particular part of current frame wil be saved in background frame and it will not detect that object further.
Increase the counter frameno .Show the final video.
