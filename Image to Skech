__CoDeR__ = 'ATX gamers'
import cv2
import numpy as np

img = cv2.imread("pic Name.jpg")

scale_percent = 0.60

width = int(img.shape[1]*scale_percent)
height = int(img.shape[0]*scale_percent)

dim = (width,height)
Original = cv2.resize(img,dim,interpolation = cv2.INTER_AREA)

kernel_sharpening = np.array([[-1,-1,-1], 
                              [-1, 9,-1],
                              [-1,-1,-1]])
sharpened = cv2.filter2D(Original,-1,kernel_sharpening)

gray = cv2.cvtColor(sharpened , cv2.COLOR_RGB2GRAY)
inv = 255-gray
gauss = cv2.GaussianBlur(inv,ksize=(15,15),sigmaX=0,sigmaY=0)

def dodgeV2(image,mask):
    return cv2.divide(image,255-mask,scale=256)
pencil_img = dodgeV2(gray,gauss)

cv2.imshow('Original',Original)
cv2.imshow('sharp',sharpened)
cv2.imshow('gray',gray)
cv2.imshow('inv',inv)
cv2.imshow('gauss',gauss)
cv2.imshow('pencil sketch',pencil_img)
#cv2.imwrite(" AT here the name of img want you in output.jpg",pencil_img)
cv2.imwrite("skech.jpg",pencil_img)
cv2.waitKey(0)
