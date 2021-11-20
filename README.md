# Steganography

## Folder Structure :
  
####  1)Exp_Images 
	The actual images
  
#### 2)Stego Image :
	The PDCT embedded images
  
#### 3)image_preparation.py : 
        a) Convert Images into YCBCR 
        b) Divides the images into 8*8 blocks
        c)Converts the 8*8 blocks back into original image
  
#### 4)data_embedding.py : 
	Embeds tha secret message in the lsb of the dct/pdct coefficients
  	
#### 5)run_stego_algorithm_PDCT.py :
        a)Prepares the pdct embedded images
        b)The file paths for the original and stego image are given in line numbers 15 and 16 inside the file 
        c)Secret message is given in line number 17
        d)alpha is given in line number 18
    
#### code to run this file :
	a)pip install bitstring
	b)python3 run_stego_algorithm_PDCT.py

#### 6)run_stego_algorithm.py :
        a)Prepares the dct embedded images
        b)The file paths for the original and stego image are given in line numbers 14 and 15 inside the file 
        c)Secret message is given in line number 16
  
#### code to run this file :
	a)pip install bitstring
	b)python3 run_stego_algorithm_PDCT.py

#### 7)extract_stego_image.py :
	a)Extract the secret message hidden inside the stego images
	b)Currently works only for the dct embedded images

#### 8)zigzag.py :
	Explnation : 

	Once each 8x8 block of the image has been transformed into DCT, “each DCT coefficient indicates the amount of a particular 
	horizontal or vertical frequency within the block. DCT coefficient (0, 0) is the DC coefficient, or average sample value. 
	Since natural images tend to vary only slightly from sample to sample, low frequency coefficients are typically larger values 
	and high frequency coefficients are typically smaller values” . Since the DC coefficient involves taking an average over the 
	entire block, modifications to this coefficient cause the most distortion in the resultant image. As such, the algorithm avoids 
	these coefficients and higher frequency (AC) coefficients that have a value close to zero or one. In order to determine which 
	coefficients correspond to AC coefficients, the transformed block is processed in what’s called the ‘zig-zag’ pattern.

	Once the DCT coefficients have been properly ordered by frequency content, the resultant matrix is then quantized in order 
	to get integer values that are more reliable for data insertion. 
