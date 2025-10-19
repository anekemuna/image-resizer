# Image Resizer Microservice

A simple Dockerized Flask microservice that resizes uploaded images to 300x300 pixels and returns the resized image.

---

## Features

- Accepts image uploads via HTTP POST
- Resizes images to 300x300 using Python’s Pillow library
- Returns the resized image as a downloadable JPEG
- Fully containerized using Docker
- Lightweight and beginner-friendly

---

## Tech Stack

- Python 3.11
- Flask
- Pillow (PIL)
- Docker

---

##  📦 Installation & Usage

### Option 1:  🔧 Build and Run Locally

#### 1. Clone the Repository

```bash
git clone https://github.com/anekemuna/image-resizer.git
cd image-resizer
```

#### 2. Build the Docker Image

```bash
docker build -t image-resizer .
```

#### 3. Run the Docker Container

```bash
docker run --rm -it -p 8085:80 image-resizer
```

> 💡 Add the `-d` flag to run the service in the background:
> `docker run --rm -d -p 8085:80 image-resizer`
> Use `docker logs <container-id>` to view logs.

The service will be available at:
`http://localhost:8085/resize`

---
### Option 2: 🐳 Use Prebuilt Docker Image from Docker Hub

If you don't want to build locally, just pull and run the image:
#### 1: Pull the Image

```bash
docker pull anekemuna/image-resizer:latest
```


#### 2. Run the Container
docker run --rm -it -p 8085:80 anekemuna/image-resizer:latest


Visit:
👉 `http://localhost:8085/resize`
---

## API Usage

### Endpoint: `POST /resize`

**Form Data:**

* `image` (file): The image file to resize

**Example using `curl`:**

```bash
curl -X POST -F "image=@your-image.jpg" http://localhost:5000/resize --output resized-filename.jpg
```

E.g.: 
```bash
curl -X POST -F "image=@pics/cat.jpeg" http://localhost:8085/resize --output resized-cat-ex.jpg

```
This saves the resized image, `resized-filename.jpg`, in your current directory.

---

## Project Structure

```
image-resizer/
├── app.py                # Flask app handling image resize
├── Dockerfile            # Container setup
├── requirements.txt      # Python dependencies
├── README.md             # You're here!
├── templates/
│   └── index.html        # Simple HTML form to test the service
├── pics/
│   └── cat.jpeg          # Test image
└── resized-cat-ex.jpg    # Example resized output

```

---

## How It Works

1. Flask receives an uploaded image through a form.
2. The image is resized to 300x300 pixels using Pillow.
3. The new image is sent back as a JPEG response.
4. Everything runs inside a lightweight Docker container.

---

## Future Enhancements

* Allow custom dimensions via query parameters
* Support multiple output formats (PNG, WEBP, etc.)
* Add basic frontend UI for uploading images
* Add logging and error handling


