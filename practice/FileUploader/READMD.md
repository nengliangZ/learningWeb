# File Uploader Module

## Traditional way

### client

Uploading a file uses `form` with `input`. (type = file)

1. use `form`

HTML forms provide three methods of encoding:

* application/x-www-form-urlencoded (the default)
* multipart/form-data
* text/plain

* use multipart/form-data when your form includes any `<input type="file">` elements
* otherwise you can use multipart/form-data or application/x-www-form-urlencoded but application/x-www-form-urlencoded will be more efficient

2. use `FormData`

```Javascript
let photo = document.getElementById("image-file").files[0];  // file from input
let req = new XMLHttpRequest();
let formData = new FormData();

formData.append("photo", photo);
req.open("POST", '/upload/image');
req.send(formData);
```

### Server

Use Formidable
Include the Formidable module to be able to parse the uploaded file once it reaches the server.

TODO:
where the file will be stored?

## Modern way

### React

```Javascript
const url = API.POST.uploadCompanyCover
const data = new FormData()
data.append('image', file)
const request = axios.post(url, data)
return {
   type: UPLOAD_COMPANYCOVER_ACTION,
   payload: request,
}
```

This will make a POST request with `form-data` format.

#### Tool for corping image: React image Crop

[React Image Crop](https://github.com/DominicTobias/react-image-crop)

### Node.js

[multer](https://github.com/expressjs/multer): Node.js middleware for handling `multipart/form-data`.
[multer-s3](https://www.npmjs.com/package/multer-s3): s3 storage for multer

### base64 and cssSprite

[base64](https://www.cnblogs.com/coco1s/p/4375774.html)
[cssSprite](https://thinking80s.iteye.com/blog/685006)
[comparision](https://zhuanlan.zhihu.com/p/24315362)
