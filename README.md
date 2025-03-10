# Dynamic Router

A lightweight, client-side dynamic routing system using Ezi.js. This project
provides seamless navigation with smooth transitions, loading indicators, and a
clean syntax for defining routes.

## Features

- **Dynamic Routing**: Load different templates based on the URL.
- **Smooth Page Transitions**: Fade-in effect for better user experience.
- **Loading Indicator**: Displays a progress bar when navigating.
- **404 Handling**: Custom 404 page for undefined routes.
- **Dark Mode Toggle**: Simple theme switcher in the settings page.

## Installation

No installation required. Just include Ezi.js from a CDN:

```html
<script src="//unpkg.com/ezi"></script>
```

## Usage

### HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Dynamic Router</title>
    <script src="//unpkg.com/ezi"></script>
    <style>
      .active {
        color: #ff5733;
        font-weight: bold;
      }
      .loading {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 3px;
        background: linear-gradient(to right, #ff5733, #ffc300);
        transform: scaleX(0);
        transform-origin: left;
        transition: transform 0.3s ease;
      }
      .loading.active {
        transform: scaleX(1);
      }
      .fade-enter {
        opacity: 0;
        transform: translateY(10px);
      }
      .fade-enter-active {
        opacity: 1;
        transform: translateY(0);
        transition: opacity 0.3s, transform 0.3s;
      }
    </style>
  </head>
  <body>
    <div id="loading-bar" class="loading"></div>
    <nav>
      <a href="" data-nav>Home</a>
      <a href="about" data-nav>About</a>
      <a href="contact" data-nav>Contact</a>
      <a href="settings" data-nav>Settings</a>
      <a href="404" data-nav>404</a>
    </nav>
    <template route="">
      <h1>Welcome Home</h1>
      <p>This is the home page</p>
    </template>
    <template route="about">
      <h1>About Us</h1>
      <p>Learn more about our company</p>
    </template>
    <template route="contact">
      <h1>Contact Us</h1>
      <form id="contact-form">
        <input type="text" placeholder="Name" required />
        <input type="email" placeholder="Email" required />
        <button type="submit">Send</button>
      </form>
    </template>
    <template route="settings">
      <h1>Settings</h1>
      <div>
        <label>
          Dark Mode
          <input type="checkbox" id="theme-toggle" />
        </label>
      </div>
    </template>
    <template route="404">
      <h1>404 - Page Not Found</h1>
      <p>Sorry, the page you're looking for doesn't exist.</p>
      <a href="" data-nav>Go Home</a>
    </template>
    <div id="root"></div>
  </body>
</html>
```

## How It Works

- Clicking navigation links updates the URL and dynamically loads the respective
  template.
- The `data-nav` attribute enables navigation without full page reloads.
- A loading indicator (`#loading-bar`) provides visual feedback.
- The `fade-enter` and `fade-enter-active` classes create smooth transitions.

## License

This project is open-source and available under the MIT License.
