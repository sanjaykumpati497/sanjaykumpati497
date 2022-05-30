import cv2
from matpotlib import pyplot as plt

# opening image
img=cv2.imread("image.jpg")
#opencv open image as RGB We'll
#also need a grayscale version
img_gray=cv2.cvtcolour(img,cv2.COLOR_BGR2GRAY)
img_gray=cv2.cvtcolour(img,cv2.COLOR_BGR2RGB)



#use min size because for not
#bothering with extra-small
#dots that wpould look like STOP signs
stop_data=cv2.cascadeclassifier('stop_data.xmi')
found=stop_data.detectmultiscale(img_gary,minsize=(20,20))


#dont do anything if there's
# no sign
amount_found=len(found)

if amount_found !=0:
    
    
    #there may be more than one
    #sign in tha image
    for(x,y,width,height) in found:
        
        #we draw a green rectngle around
        #every recognised sign
        cv2.rectangle(img_rgb,(x,y),
                     (x+height,y+width),
                     (0,255,0), 5)
                     
#creates the environment of
#the picture and shows it
plt.subplot(1,1,1)
plt.imshow(img_rgb)
plt.show()
