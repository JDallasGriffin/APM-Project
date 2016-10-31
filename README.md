# Advanced Predictive Modeling - Project Charter

Group: Brooks Beckelman | Dallas Griffin | Davis Townsend | Estevan Gonzalez | Sean Kessel | Zackery Bilderback

# Project Summary

_Popspots – a start-up specializing in digital point-of-purchase (PoP) advertisement systems – is interested in developing a new add-on service: automating the re-stock process of racks in check-out lanes for their clients in the grocery industry. Our project would be to leverage deep learning and an archive of images captured by Popspots devices to implement a SKU identifier as a first step towards meeting Popspots business objective._

## Popspots Background

Popspots is a startup based out of Austin, Texas focused on developing point-of-purchase advertisement systems. They work with grocers &amp; retailers to install tablets in check-out aisles then sell advertisements (still images and/or videos) in 7-second increments on the marketplace. Using proprietary technology, they offer dynamic ad slots for specific regions or locations that only run and charge when customers are in the check-out aisle.

## Business Case

The PoP rack is a major revenue generator for retailers – netting on average $24,000 in revenue per rack per annum. Retailers face a significant challenge keeping their PoP racks stocked and in compliance with product placement agreements. Assuming 10% revenue leakage due to stock-outs, an automated system capable of tracking both SKU location and stock would generate up to $2,400 in additional sales and $1,500 in additional profit per rack per annum. Additionally, a stock checking service would help ensure all product placement agreements with vendors are in compliance as well as provide valuable analytics for optimizing product placement and mix.

Popspots already has tablets with cameras pointed directly at racks used primarily for customer &quot;look&quot; tracking. A stock check service would therefore incur limited costs beyond its development and position well with the company&#39;s long-term strategy of leveraging innovative technology to create value at retailers&#39; points of purchase.

## Objectives

- _Primary_: Develop Neural Net that can accurately segment an image of a rack into its component SKUs
- _Stretch_: Refine Neural Net to map segments images to their corresponding SKUs (i.e. snickers, kit-kats, etc..)
- _Future State_: Further refine to estimate the stock level of an SKU (i.e. &quot;fully stocked&quot;, &quot;almost out&quot;, &quot;out of stock&quot;) and link with automated (or semi-automated) restock system

## Data Scope

- 4 images per day of 25 racks at 10 grocery stores taken over 10 Business Days (~1,000 total images)
- ~30 SKUs per rack (~30,000 SKUs)
- Raw pixels per image: 640 x 480
- Pixels in raw dataset: 307,200,000
- Training data of ~10 images per unique SKU.
  - NOTE: Due to project time constraints we may limit the number of unique SKUs to be considered for identification.

# Approach

## Feature Engineering

1. Convert images to features in Python and perform all necessary data transformations
2. Scrape images off web of in-scope unique SKUs and convert to training set

## Modeling

1. Model: Deep Neural Net
2. Stage 1 – SKU Segmentation
  1. Identify &quot;rack&quot; and crop-out background
  2. Potentially reject poor photos
    1. NOTE: Popspots software already does not save images if people obstructing photo
  3. Segment image of racks into component SKUs
  4. NOTE: Parts A &amp; B can be done manually for a reduced sample size if their too technically challenging for the scope of the project
3. Stage 2 _(time permitting)_ – SKU Identification
  1. Train neural net using images scraped from web on in-scope SKUs
  2. Use neural net to identify in-scope SKUs from the individual images of SKUs segmented in Stage 1

# Resources

- Pop Spots URL: [https://www.popspotsadvertising.com/](https://www.popspotsadvertising.com/)
- Sample Web-Scraping Code for Training Data: [http://blog.yhat.com/posts/image-classification-in-Python.html](http://blog.yhat.com/posts/image-classification-in-Python.html)
- How to setup Tensorflow on WINDOWS: https://gist.github.com/ericjang/959c03168c0bdfac1ca3
- How to setup OpenCV on WINDOWS: http://docs.opencv.org/master/d5/de5/tutorial_py_setup_in_windows.html
- Deep Learning Notebooks: https://github.com/kjw0612/awesome-deep-vision
- TensorFlow Examples: https://github.com/aymericdamien/TensorFlow-Examples
- Edge-based segmentation example: http://scikit-image.org/docs/dev/auto_examples/applications/plot_coins_segmentation.html
- Python implementation of TensorFlow Example: https://github.com/Russell91/tensorbox/blob/master/evaluate.ipynb

NOTE: Both TensorFlow & OpenCV can be run from Jupyter Notebooks.
