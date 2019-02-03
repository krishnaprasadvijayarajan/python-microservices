# python-microservices
simple microservices

Your task is to build a simple microservice using the Python Flask framework.  This microservice should be responsible for uploading and downloading typical types of files (txt, pdf, png, jpg, etc.).

## Requirements

1. /upload
    - Uploads one file at a time.  Feel free to define what the payload looks like.  You can go ahead and persist the files to the filesystem somewhere.

2. /download
    - Retrieves and downloads a single file, using the filename as the key.

3. We will be looking at understanding of web services fundamentals, including usage of appropriate error response.
    — You should force a failure condition to demonstrate.
    
4. We will also be looking more broadly at Python code structure, layout, and other best practices.

5. Feel free to incorporate whatever else you feel appropriate and feasible.

6. Finally, please provide a way to install dependencies and run/test the app.

## Design

1. `http://localhost:5000/` will redict to `http://localhost:5000/upload`
    - This page will list all uploaded files. And you can upload a file using UI.
    - Or you can use curl to upload a file.
    ```
    curl -i -X POST -H "Content-Type: multipart/form-data" -F "file=@/path/to/file/sample.pdf" http://localhost:5000/upload
    ```
    
2. When file upload fails, the error will show and a link to `upload` will be provided
    - The upload file should have an extension.
    - Only these extension will be allowed. `txt`, `rtf`, `doc`, `docx`, `xls`, `xlsx`, `pdf`
    - The upload file name should be unique in the download folder of server.
    - If upload file has any of the above issue, the server will show the corresponding error.

3. Upload file using API endpoint `http://localhost:5000/upload/your-upload-file-name.ext`
    - You can use curl or your program to upload file
    ```
    curl -i -X POST -H "Content-Type: application/json" --data-binary "@/Users/austinjung/Documents/sample.pdf" http://localhost:5000/upload/my_upload.pdf
    ```
    
4. You can get all file names using API `http://localhost:5000/download`
    - You can use curl or your program to get file names
    ```
    ```
    - And the response will be
    ```
    [
{
"filename": "Austin-Jung_2019_resume.pdf",
"url": "http://localhost:5000/download/Austin-Jung_2019_resume.pdf"
},
{
"filename": "sample.pdf",
"url": "http://localhost:5000/download/sample.pdf"
}
]
```


## Deployment

1. This project repository is [https://bitbucket.org/austinjung/asyncproxyinpython](https://bitbucket.org/austinjung/asyncproxyinpython)
2. The project repository is linked with [Austin's Docker Cloud](https://cloud.docker.com/swarm/austinjung/repository/registry-1.docker.io/austinjung/async-http-proxy-python/general)
3. In your docker, run the following line.
    ```
    $ docker run -p 8080:8080 austinjung/async-http-proxy-python:latest
    ```
    or 
    ```
    clone the project repository
    cd /to/the_top_folder_of_the_project
    $ docker-compose up
    ```

## Things do-to

1. Some images or contents are blocked by 'Referrer Policy: no-referrer-when-downgrade', 'Access-Control-Allow_Origin', or 'cross-origin frame' etc.
2. Do proper post method.
and more
