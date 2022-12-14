Main source

https://github.com/tesseract-ocr/tessdoc


1. Create folder structure
	```
	Mkdir data
	Mkdir data/tessdata
	```

2. Pull the image from Docker Hub: 
    ```
	docker pull clearlinux/tesseract-ocr
    ```

3. Download `eng.traineddata` from https://github.com/tesseract-ocr/tessdata and put it into `data/tessdata/eng.traineddata`

4. Put the source image into img.jpg `data/img.jpg`

5. Run
    ```
	docker run --rm -it --name tesseract -e "TESSDATA_PREFIX=/data/tessdata" -v /Users/ikatkov/non-work-projects/tesseract/data/:/data -w /data clearlinux/tesseract-ocr tesseract img.jpg stdout --oem 1
    ```

	or
    ```
	docker run --rm -it --name tesseract -e "TESSDATA_PREFIX=/data/tessdata" -v /Users/ikatkov/non-work-projects/tesseract/data/:/data -w /data clearlinux/tesseract-ocr tesseract img.jpg stdout --oem 1 --psm 6
    ```

5. Optionally create a config as mentioned in https://github.com/gabrielpc1190/tesseract-ocr


Open the image in mac preview app. Crop the PCB to a single IC. Rotate to make the text horizontal. Don't save. Run the extraction tool in a separate terminal. Undo the crop/rotation. Rinse and repeat.
