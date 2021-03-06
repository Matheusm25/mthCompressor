# MTH Text Compressor

  This is a text compressor that I made based on Huffman coding, where I turn the characters in the file to bits, in a way that I can do
  the reverse process.
  
## How it works:

  When running the mthCompressor.py program and passing the filename (and extension) as parameters, it will know if it should compress
  or decompress. The compressor will store the different characters of the file and assign a binary value to each one of them. After 
  that it changes the characters by their respective binary values.   
 
  However, the decompressor needs a information inside the binary sequence generated by the compressor in order to know what each binary
  word means. I named this information "key", the key is a binary sequence of 255 bits, for each positive bit in that sequence I have a
  compatible character in the file. The decompressor will use this "key" to know which characters are in the file and also generate a 
  list of bits that are the representations of the characters, after that we can change the bits by the characters and we will have the 
  text decompressed again.
  
## How much does it compress?
  
  Disregarding the space occupied by the "key" (255 bits), the compressor can decrease the size of the file based on the number of bits
  that each character have.
  
    R = (E / 8) * 100
  
  Where:    
  E = the entropy in the compression of the file (also know as the number of bits in each character).   
  R = the reduction of the file in percentage.
  
  But we can't forget about the space that the "key" take. The default space it occupies is 255 bits, however, due to the need to have a
  file with a size (in bits) multiple of 8, I have to add extra bits.
  
    A = (255 + (Q * E)) % 8
    
  Where:   
  A = bits that will be placed at the beginning of the key.   
  Q = number of characters in the file.   
  E = the entropy in the compression of the file (also know as the number of bits in each character).   
  * The % simbol means Modulus - remainder of the division of left operand by the right.
  
  The "key" will have the size of:
    
    K = A + 255
  
 Where:   
 K = key size.
  
 The final size of the file will be: 
 
    S = ((E * B) + K) / 8
 
 Where:   
 B = the initial size of the file (in Bytes).   
 S = the final size of the file (in Bytes).
 
 The percentage reduction is:
 
    R = ((B - S) / B) * 100
  
  
  
