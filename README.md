<p align="center">
  <h3 align="center">
  A unified toolkit for Deep Learning Based Document Image Analysis
  </h3>
</p>

---

## What is Layout-Extractor

![Example Usage](https://github.com/Layout-Parser/layout-parser/raw/main/.github/example.png)

Layout-Extractor aims to provide a wide range of tools that aims to streamline Document Image Analysis (DIA) tasks. Here are some key features:

- Layout-Extractor provides a rich repository of deep learning models for layout detection as well as a set of unified APIs for using them. For example, 
  
  <details>
  <summary>Perform DL layout detection in 4 lines of code</summary>
  
  ```python
  import layoutextractor   as lp
  model = lp.AutoLayoutModel('lp://EfficientDete/PubLayNet')
  # image = Image.open("path/to/image")
  layout = model.detect(image) 
  ```
  
  </details>

- LayoutParser comes with a set of layout data structures with carefully designed APIs that are optimized for document image analysis tasks. For example, 

  <details>
  <summary>Selecting layout/textual elements in the left column of a page</summary>
  
  ```python
  image_width = image.size[0]
  left_column = lp.Interval(0, image_width/2, axis='x')
  layout.filter_by(left_column, center=True) # select objects in the left column 
  ```
  
  </details>

  <details>
  <summary>Performing OCR for each detected Layout Region</summary>
  
  ```python
  ocr_agent = lp.TesseractAgent()
  for layout_region in layout: 
      image_segment = layout_region.crop(image)
      text = ocr_agent.detect(image_segment)
  ```
  
  </details>  
    
  <details>
  <summary>Flexible APIs for visualizing the detected layouts</summary>
  
  ```python
  lp.draw_box(image, layout, box_width=1, show_element_id=True, box_alpha=0.25)
  ```
  
  </details>  
    
  </details>  
    
  <details>
  <summary>Loading layout data stored in json, csv, and even PDFs</summary>
  
  ```python 
  layout = lp.load_json("path/to/json")
  layout = lp.load_csv("path/to/csv")
  pdf_layout = lp.load_pdf("path/to/pdf")
  ```
  
  </details>

- LayoutParser is also a open platform that enables the sharing of layout detection models and DIA pipelines among the community. 
  

## Examples 

We provide a series of examples for to help you start using the layout parser library: 

1. [Table OCR and Results Parsing](https://github.com/Layout-Parser/layout-parser/blob/main/examples/OCR%20Tables%20and%20Parse%20the%20Output.ipynb): `layoutextractor` can be used for conveniently OCR documents and convert the output in to structured data. 

2. [Deep Layout Parsing Example](https://github.com/Layout-Parser/layout-parser/blob/main/examples/Deep%20Layout%20Parsing.ipynb): With the help of Deep Learning, `layoutextractor` supports the analysis very complex documents and processing of the hierarchical structure in the layouts. 

