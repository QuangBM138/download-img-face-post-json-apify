# Bulk Image Downloader from JSON

A simple and efficient web tool to download bulk images from Facebook posts using Apify's Facebook Photos Scraper. This tool converts JSON data from Apify into downloadable image files packaged in a ZIP archive.

## 🌐 Live Demo
Visit the web application here: **[https://download-img-face-post-json-apify.vercel.app/](https://download-img-face-post-json-apify.vercel.app/)**

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [How It Works](#how-it-works)
- [Step-by-Step Guide](#step-by-step-guide)
- [Troubleshooting](#troubleshooting)
- [Technology Stack](#technology-stack)

## 🎯 Overview

This project is designed to streamline the process of extracting and downloading multiple images from Facebook posts. It combines:
1. **Apify** - A powerful web scraping platform
2. **Facebook Photos Scraper** - An Apify actor that extracts photo data from Facebook posts
3. **This Web Tool** - Converts JSON output into downloadable images

## ✨ Features

- **Simple JSON Input**: Paste JSON data directly into the web interface
- **Real-time Preview**: View all detected images before downloading
- **Batch Download**: Download all images as a single ZIP file
- **User-friendly UI**: Clean, modern interface built with Tailwind CSS
- **Automatic Error Handling**: Gracefully handles invalid JSON and failed downloads
- **CORS Support**: Works with most image sources including Facebook CDN

## 📦 Prerequisites

Before using this tool, you'll need:
1. An **Apify account** (free or paid) - [Sign up here](https://apify.com)
2. Access to **Facebook Photos Scraper** from Apify Store
3. A **Facebook post URL** that you want to extract images from
4. Basic understanding of JSON format

## 🔄 How It Works

```
Facebook Post (73 images)
          ↓
    Apify Scraper
    (facebook-photos-scraper)
          ↓
    JSON Output
    (array of image objects)
          ↓
    This Web Tool
    (parse & download)
          ↓
    ZIP File
    (all images bundled)
```

## 📖 Step-by-Step Guide

### Step 1: Login to Apify

1. Go to [https://apify.com](https://apify.com)
2. Sign in with your account (or create one if you don't have it)

### Step 2: Find Facebook Photos Scraper

1. Navigate to **Apify Store**
2. Search for **`facebook-photos-scraper`**
3. Click on the actor to open it

### Step 3: Configure the Scraper

1. **Enter the Facebook Post URL**: Paste the link of the Facebook post you want to scrape
   - Example: `https://www.facebook.com/.../posts/...`

2. **Set the Number of Images**:
   - Check how many images are in the post (e.g., 73 images)
   - **Important**: Set the image limit **higher than the actual count** to ensure all images are captured
   - Example: If the post has **73 images**, set it to **75**
   - This buffer prevents missing images due to loading delays or API limitations

### Step 4: Run the Scraper

1. Click the **"Start"** or **"Run"** button
2. Wait for the scraper to complete (this may take a few minutes depending on the number of images)
3. Once completed, you'll see the results in JSON format

### Step 5: Adjust JSON Display Limit (if needed)

1. By default, Apify may limit the preview to **50 items**
2. If you have more than 50 images (e.g., 73), you need to increase this limit:
   - Look for the **display limit** or **max results** setting in Apify
   - Change it to a higher number (e.g., **100** for 73 images)
3. This ensures all image data is visible in the output

### Step 6: Copy the JSON Output

1. Select all the JSON data from the Apify results
2. Copy it to your clipboard
3. Example JSON structure:
   ```json
   [
     {"image": "https://example.com/image1.jpg"},
     {"image": "https://example.com/image2.jpg"},
     {"image": "https://example.com/image3.jpg"}
   ]
   ```

### Step 7: Use This Web Tool

1. Visit **[https://download-img-face-post-json-apify.vercel.app/](https://download-img-face-post-json-apify.vercel.app/)**
2. **Paste the JSON** into the text area
3. Click **"Parse & Preview"** button
4. The tool will:
   - Validate the JSON format
   - Extract all image URLs
   - Display a preview grid of all images
5. If the preview looks correct, click **"Download All (.ZIP)"**
6. Your browser will download a ZIP file containing all images

### Step 8: Extract and Use

1. Save the ZIP file to your desired location
2. Extract the ZIP archive
3. All images will be named as `image_1.jpg`, `image_2.jpg`, etc.
4. Use them as needed!

## 📝 Complete Example

**Input JSON:**
```json
[
  {"image": "https://scontent-fra1-1.xx.fbcdn.net/..."},
  {"image": "https://scontent-fra1-1.xx.fbcdn.net/..."},
  {"image": "https://scontent-fra1-1.xx.fbcdn.net/..."}
]
```

**Output:** A ZIP file with all images bundled together

## 🐛 Troubleshooting

### Issue: "Invalid JSON format" error

**Solution:**
- Ensure the JSON is properly formatted (valid array of objects)
- Check for trailing commas or extra characters
- Copy the entire output, including brackets `[]`

### Issue: "No valid image URLs found"

**Solution:**
- Verify that the JSON contains an `"image"` field
- Check that the image URLs are valid and not empty
- Make sure you're using the correct JSON structure

### Issue: Some images fail to download

**Solution:**
- This may be due to temporary network issues or image availability
- The tool will skip failed downloads and continue with others
- Try downloading again

### Issue: ZIP file is too large

**Solution:**
- This is normal for large image batches
- Consider downloading in smaller batches if needed
- Ensure you have enough disk space

### Issue: Images appear broken in preview

**Solution:**
- This is often a CORS (Cross-Origin Resource Sharing) limitation
- **The images will still download correctly** even if they show broken in the preview
- The actual download bypasses these restrictions

## 🛠️ Technology Stack

- **Frontend**: HTML5, Tailwind CSS, JavaScript
- **Libraries**:
  - [Tailwind CSS](https://tailwindcss.com/) - Styling
  - [JSZip](https://stuk.github.io/jszip/) - ZIP file creation
  - [FileSaver.js](https://github.com/eligrey/FileSaver.js) - File download support
- **Hosting**: Vercel
- **Data Source**: Apify API

## 📄 Tips & Best Practices

1. **Verify Image Count**: Always check the actual number of images in a Facebook post before setting the Apify limit
2. **Use Buffer**: Add 2-5 extra images to your limit to avoid missing any data
3. **Check JSON Structure**: Ensure the JSON output contains the `image` field with valid URLs
4. **File Organization**: Organize downloaded images in folders by date or source post
5. **Privacy**: Respect copyright and privacy laws when downloading images

## ❓ FAQ

**Q: Does this tool require any installation?**
A: No! It's a web-based tool. Just visit the URL and start using it immediately.

**Q: Can I download images from other sources besides Facebook?**
A: Yes, as long as you have JSON data with the `image` field and valid URLs.

**Q: Is there a limit to how many images I can download at once?**
A: Not on the web tool side, but Apify may have limits depending on your subscription. Check Apify's documentation.

**Q: Are my images stored on the server?**
A: No! All processing happens in your browser. Images are downloaded directly to your computer.

**Q: Can I use this with other scraping tools besides Apify?**
A: Yes, as long as the output JSON has the same structure with an `image` field.

## 🤝 Contributing

If you have suggestions or find bugs, feel free to create an issue or submit a pull request!

## 📄 License

This project is open-source. Feel free to use, modify, and distribute as needed.

## 💡 Support

If you encounter any issues or have questions:
1. Check the Troubleshooting section above
2. Verify your JSON format
3. Ensure you're using a modern web browser
4. Try clearing your browser cache

---

**Happy downloading! 🎉**

For more information about Apify, visit: [https://apify.com](https://apify.com)
