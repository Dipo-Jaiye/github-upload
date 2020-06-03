```python
from PIL import Image
b = (0,0,0)
y = (255,255,0)
face = [[b,b,b,b,y,y,b,b,b,b],
        [b,b,y,y,y,y,y,y,b,b],
        [b,y,y,y,y,y,y,y,y,b],
        [b,y,y,b,y,y,b,y,y,b],
        [y,y,y,y,y,y,y,y,y,y],
        [y,y,b,y,y,y,y,b,y,y],
        [b,y,y,b,b,b,b,y,y,b],
        [b,y,y,y,y,y,y,y,y,b],
        [b,b,y,y,y,y,y,y,b,b],
        [b,b,b,b,y,y,b,b,b,b]]

smiley = Image.new("RGB", (10,10))
width, height = smiley.size

for row in range(height):
    for col in range(width):
        smiley.putpixel((col, row), face[row][col])
smiley = smiley.resize((500,500))
        
smiley.show()
```


```python
im = Image.open('DR.bmp') #path to image file

width, height = im.size

resolution = width * height

print("The image resolution is: ", width, " x ", height)
print("The resolution is: ", resolution)
```

    The image resolution is:  130  x  130
    The resolution is:  16900
    


```python
bitd = [1,2,8,16,24]
print("The file sizes are")
for i in bitd:
    a = resolution * i
    print(a/1024)
```

    The file sizes are
    16.50390625
    33.0078125
    132.03125
    264.0625
    396.09375
    


```python
12*24/8

```




    36.0




```python
16*3000*3000/8/1024/1024

```




    17.1661376953125




```python
6*32*16
```




    3072




```python
from PIL import Image

b = (0,0,0)
y = (255,255,0)

face = [[b,b,b,b,y,y,b,b,b,b],
        [b,b,y,y,y,y,y,y,b,b],
        [b,y,y,y,y,y,y,y,y,b],
        [b,y,y,b,y,y,b,y,y,b],
        [y,y,y,y,y,y,y,y,y,y],
        [y,y,b,y,y,y,y,b,y,y],
        [b,y,y,b,b,b,b,y,y,b],
        [b,y,y,y,y,y,y,y,y,b],
        [b,b,y,y,y,y,y,y,b,b],
        [b,b,b,b,y,y,b,b,b,b]]

scale = 50

scaled = Image.new("RGB", (scale * 10, scale * 10))

width, height = scaled.size

for row in range(height):
    for col in range(width):
        scaled.putpixel((col,row), face[int(row/scale)][int(col/scale)])


scaled.show()
```


```python
original = Image.open('puppy.bmp')

width, height = original.size
scale = 2

e = Image.new('RGB', (scale * width, scale * height))
e_w, e_h = e.size
r = Image.new('RGB', (e_w, e_h))

for y in range(height):
    for j in range(width):
        pixel = original.getpixel((j,y))
        
        e.putpixel((int(j/scale),int(y/scale)),pixel)
        r.putpixel((j,height - y - 1), pixel)
        
r.show()
```


```python

```


```python

```


```python

```


```python
original = Image.open('puppy.bmp')

width, height = original.size
scale = 2

e = Image.new('RGB', (scale * width, scale * height))
e_w, e_h = e.size

for y in range(height):
    for x in range(width):
        pixel = original.getpixel((x,y))
for a in range(e_h):
    for b in range(e_w):
        e.putpixel((b,a),pixel)
e.show()
```


```python
#Negative filter
im = Image.open('image.png')

rgb_im = im.convert('RGB')

width, height = im.size

out = Image.new('RGB', (width, height))

for row in range(height):
    for col in range(width):
         r, g, b = rgb_im.getpixel((col, row))
         out.putpixel((col, row), (255 - r, 255 - g, 255 - b))

out.show()
```


```python
#Lighten filter
im = Image.open('image.png')

rgb_im = im.convert('RGB')

width, height = im.size

out = Image.new('RGB', (width, height))

for row in range(height):
    for col in range(width):
         r, g, b = rgb_im.getpixel((col, row))
         out.putpixel((col, row), (min(255,r*2),min(255,g*2),min(255,b*2)))

out.show()
```


```python
#Sepia filter
im = Image.open('image.png')

rgb_im = im.convert('RGB')

width, height = im.size

out = Image.new('RGB', (width, height))

for row in range(height):
    for col in range(width):
         r, g, b = rgb_im.getpixel((col, row))
         out.putpixel((col, row), (
             min(255, int((0.393*r) + (0.769*g) + (0.189*b))), 
             min(255, int((0.349*r) + (0.686*g) + (0.168*b))), 
             min(255, int((0.272*r) + (0.534*g) + (0.131*b)))
                     ))

out.show()
```


```python
#Pixelate
im = Image.open('image.png')

rgb_im = im.convert('RGB')

width, height = im.size

out = Image.new('RGB', (width, height))

pixelAmount = int(input('Enter the pixelation level: '))

for row in range(0, height - pixelAmount, pixelAmount):
    for col in range(0, width - pixelAmount, pixelAmount):
        r, g, b = rgb_im.getpixel((col, row))
        for o in range(row, row + pixelAmount):
            for p in range(col, col + pixelAmount):
                out.putpixel((p,o), (r,g,b))

out.show()
```

    Enter the pixelation level: 6
    


```python
#B/W filter
```


```python
#Greyscale filter
```


```python
#Clarendon filter
#lights are lighter, darks are darker, blue tint)
```


```python
#Hiding a message in an image
#path to image to hide within here
image = Image.open('images/image.png')
rgb_image = image.convert('RGB') #convert to RGB

width, height = image.size #assign the image width and height to variables
message = input("What message do you want to hide?")

#I'm going to use the message "hello everybody!" as an example

binary_message = ""

#The for loop will repeat for each character of "hello everybody!", including the space and the exclamation mark

for char in message:
    ascii_number = ord(char) #This converts the ASCII character into the denary number that represents it
                             #For the first letter, 'h', this gives '104'
                             
    bin_as_string = bin(ascii_number) #This converts that denary number into a string representing a binary number
                                      #So '104' is converted into the string '0b1101000'
                                      #The 'b' is added in by 'bin()' to show the number is binary
                                      
    bin_as_string = bin_as_string.replace('b','') #This removes the 'b'
                                                  #So finally you get '01101000'
    
    while len(bin_as_string) < 8 :
        bin_as_string = '0' + bin_as_string #This lengthens the binary number string until it is 8 bits
                                            #Our example is already 8 bits long, so it remains '01101000'

    binary_message = binary_message + bin_as_string #This result is then added to the binary message
```


```python
#Create a grid for the output image
output_image = Image.new('RGB', (width,height))

#Create a variable to keep track of how far through the binary message the code has got
i = 0

#Set up loops to modify each pixel within the image
for row in range(height):
    for col in range(width):
        r, g, b = rgb_image.getpixel((col, row))

        #Start by converting the red value of the pixel to binary  
        bin_r = bin(r)    
        
        #If the binary message has not been completely encoded, the code does the following things
        if i < len(binary_message):     
             
            
            #Replace the final bit with a 1 or a 0 from the message    
            if binary_message[i] == '1':
                bin_r = bin_r[:-1] + '1'
            else:
                bin_r = bin_r[:-1] + '0'
                
        #Once the message has been completely encoded, the code replaces every red value's last bit with a zero
        #This isn't good steganography, but it's simple to implement
        else:
            bin_r = bin_r[:-1] + '0'
            
        #The binary number for the red value is converted back to an integer
        new_r = int(bin_r,2)
        
        #This integer is set as the pixel's red value
        output_image.putpixel((col, row), (new_r,g,b))
        
        #The variable i is increased by 1 to move on to the next binary character of the message
        i = i + 1

#Once the code has iterated over all pixels in the image to change their red values, the image is saved
output_image.save("encoded_image.png")
```


```python
output_bits = ""
output_text = ""

#Set up loops to address each pixel in the image
for row in range(height):
    for col in range(width):
      r, g, b = rgb_image.getpixel((col, row))
      bin_r = bin(r)
        
end = False
while end == False:
    byte = int(output_bits[:8],2)
    print(byte)
    if byte == 0:
        end = True
    else:
        output_text = output_text + chr(byte)
        output_bits = output_bits[8:]

print(output_text)
```


```python
#Run length Encoding

from re import sub

def encode(text):
    return sub(r'(.)\1*', lambda m: str(len(m.group(0))) + m.group(1),text)

def decode(text):
    return sub(r'(\d+)(\D)', lambda m: m.group(2) * int(m.group(1)),text)

raw = 'bbbbyybbbbbbyyyyyybbbyyyyyyyybbyybyybyybyyyyyyyyyyyybyyyybyybyybbbbyybbyyyyyyyybbbyyyyyybbbbbbyybbbb'
e_raw = encode(raw)
print(decode(raw))
```

    bbbbyybbbbbbyyyyyybbbyyyyyyyybbyybyybyybyyyyyyyyyyyybyyyybyybyybbbbyybbyyyyyyyybbbyyyyyybbbbbbyybbbb
    


```python
from PIL import Image
im = Image.open('puppy.bmp')
im.save('puppy.jpg',"JPEG", quality=100)
```


```python

```
