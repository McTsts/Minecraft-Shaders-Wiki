# Random notes that relate to using shaders

### Preserving RGB
basically anything to do with images in js does alpha premultiplying, which ruins rgb values when alpha is anything less than 255. afaik only way to not suffer this is to directly interact with the raw file instead of as an image. so if you wanted to send an image with alpha to someone over discord or something, don't send it as an image. instead, you can change the file extension so discord treats it as some unknown file, or zip it and send the zip to preserve data.
