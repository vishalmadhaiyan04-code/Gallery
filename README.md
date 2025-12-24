# Ex.08 Design of Interactive Image Gallery
# Date:16/11/2024
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
  ## views.py
  
from django.shortcuts import render
def gall(request):
    return render(request,"gallery.html")
```
```
  ## urls.py

from django.contrib import admin
from django.urls import path
from gall import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('gallary/',views.gall),
]
```
```
## gallery.html

{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Photo Gallery</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color:black;
        }

        h1 {
            text-align: center;
            padding: 20px;
            color:beige;
        }

        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 15px;
            padding: 20px;
        }

        .gallery img {
            height: auto;
            width: 100%;
            cursor: pointer;
            border-radius: 70px;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .gallery img:hover {
            transform: scale(1.15);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            position: relative;
            max-width: 90%;
            max-height: 80%;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .modal img {
            max-width: 100%;
            max-height: 100%;
            border-radius: 8px;
        }

        .modal .close {
            position: absolute;
            top: 20px;
            right: 30px;
            font-size: 30px;
            cursor: pointer;
            z-index: 10;
            color: beige;
        }

        .modal .prev, .modal .next {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            font-size: 40px;
            cursor: pointer;
            user-select: none;
            z-index: 10;
            color: beige;
        }

        .modal .prev {
            left: 20px;
        }

        .modal .next {
            right: 20px;
        }
    </style>
</head>
<body>
    <h1>Interactive Photo Gallery</h1>
    <div class="gallery">
        <img src="{% static 'image/image1.jpg' %}" alt="Photo 1">
        <img src="{% static 'image/imag3.jpg' %}" alt="Photo 2">
        <img src="{% static 'image/imag2.jpg' %}" alt="Photo 3">
        <img src="{% static 'image/image3.jpg' %}" alt="Photo 4">
        <img src="{% static 'image/image2.jpg' %}" alt="Photo 5">
        <img src="{% static 'image/imag1.jpg' %}" alt="Photo 6">
        <img src="{% static 'image/image4.jpg' %}" alt="Photo 7">
        <img src="{% static 'image/image5.jpg' %}" alt="Photo 8">
    </div>

    <div class="modal" id="modal">
        <span class="close" id="close">&times;</span>
        <span class="prev" id="prev">&#10094;</span>
        <div class="modal-content">
            <img id="modalImg">
        </div>
        <span class="next" id="next">&#10095;</span>
    </div>

    <script>
        const images = document.querySelectorAll('.gallery img');
        const close = document.getElementById('close');
        const prev = document.getElementById('prev');
        const next = document.getElementById('next');

        let currentIndex = 0;

        function showModal(index) {
            currentIndex = index;
            modal.style.display = 'flex';
            modalImg.src = images[currentIndex].src;
        }

        function hideModal() {
            modal.style.display = 'none';
        }

        function showNext() {
            currentIndex = (currentIndex + 1) % images.length;
            modalImg.src = images[currentIndex].src;
        }

        function showPrev() {
            currentIndex = (currentIndex - 1 + images.length) % images.length;
            modalImg.src = images[currentIndex].src;
        }

        images.forEach((img, index) => {
            img.addEventListener('click', () => showModal(index));
        });

        close.addEventListener('click', hideModal);

        window.addEventListener('click', (e) => {
            if (e.target === modal) {
                hideModal();
            }
        });

        next.addEventListener('click', showNext);
        prev.addEventListener('click', showPrev);

        document.addEventListener('keydown', (e) => {
            if (modal.style.display === 'flex') {
                if (e.key === 'ArrowRight') {
                    showNext();
                } else if (e.key === 'ArrowLeft') {
                    showPrev();
                } else if (e.key === 'Escape') {
                    hideModal();
                }
            }
        });
    </script>
</body>
</html>
```
# OUTPUT:

![Screenshot 2024-12-13 232006](https://github.com/user-attachments/assets/ca4573d0-77e4-410e-920e-ff810f133d9e)

![image](https://github.com/user-attachments/assets/4d3bc3d6-d34a-4aba-bcb6-dbba152152fd)

![image](https://github.com/user-attachments/assets/43ba704c-cc52-4c82-a0ea-720f7120bfb3)

# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
