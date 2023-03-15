---
title: "NoPixel Purple Storefronts Map"
excerpt: "A website built on Vite + React w/ Supabase as a database."
header:
  image: /assets/images/portfolio/np-purple-storefronts/big/storefront_map_overview_image.png
  teaser: /assets/images/portfolio/np-purple-storefronts/thumb/project-listing-icon.png
sidebar:
  - title: "Website"
    image: /assets/images/portfolio/np-purple-storefronts/big/example_storefront.png
    image_alt: "Example Storefront on Map"
    text: "<a href='https://gamenew09.com/np-purple-storefronts' target='_blank'>https://gamenew09.com/np-purple-storefronts</a>"
  - title: "Repository"
    text: "<a href='https://github.com/gamenew09/np-purple-storefronts' target='_blank'>https://github.com/gamenew09/np-purple-storefronts</a>"
---

This project, while running fine, is currently being updated consistently. Some changes made may not be reflected in this portfolio yet.
{: .notice--warning}

This website is a project that I made for LSBN as Roy Wilson on NoPixel Purple. The website is a map of storefront markers that describe not only location but also its name, short description, and images relating to the storefront. People can login using their Discord account, and if they have permission, add new storefronts or edit existing ones as needed.

A [previous version of this project](https://github.com/gamenew09/np-purple-storefronts-old) was based from [np-gangmap](https://github.com/skyrossm/np-gangmap) (although I found out about this through [purple-turfmap](https://github.com/nopixelpublic/purple-turfmap)). However, I was getting tired of editing json files just to add another storefront, especially since storefronts were getting added left and right. So, I decided to recode it using Vite + React along with Supabase as the database backbone.

## (Semi-)Technical Details
### Frontend
The storefront map uses React for creating the frontend. I used [react-leaflet](https://github.com/PaulLeCam/react-leaflet) and [Leaflet](https://leafletjs.com) for the map. The map layer that shows the entirety of San Andreas is just the tiles pre-made in np-gangmap. I heavily relied on [Tailwind CSS](https://tailwindcss.com/) and [daisyUI](https://daisyui.com/) for styling everything from the topbar to the carousel on each marker. Tailwind CSS lets you apply css styles via classes while daisyUI uses Tailwind to create standard components that can be rendered just be applying classes.

### Backend
For the backend, I used [Supabase](https://supabase.com/) which let me make this project with no cost. There are 4 tables that I created for this project to happen:

#### `permissions`
This table holds the `user_id` of a user that can edit & create storefronts, and their images.

#### `storefront_categories`
This table holds data about a category of storefronts. It has the title of the category, whether or not the category is considered a general category, and the Font Awesome icon that should be used as the marker icon on the map.

A general category will display not only the storefronts that belong to this category, but also any storefronts that have no category attached to it.

#### `storefront_images`
This table holds the images that are displayed on the carousel for all storefronts. The table has a description, the url to the image (which is usually just an imgur link or other image hosting platform), and the character in NoPixel Purple that took the picture. The row links to a storefront's id, which allows the carousel to actually show images relating to the opened storefront.

#### `storefronts`
This table holds data about a storefront within the city. It has a title, description, location encoded in json, creation time, and an owner_id (which is currently a useless column).