# What is OCR?
Optical Character Recognition - Converts image containing text into a machine readable text format. 

# How does it work?
Solved via a combination of hardware/software. 
Camera or scanner is used to capture the data.
Image processing used to pre-process the image = smooth/descale. 
Model used to extract the text from the image. 
Extracted text is post-processed. Provides a text or pdf.

There are four stages:
Image acquisition - capture data in a binary format. 

Pre-processing - cleans the image and removes noise, e.g. de-skewing, de-speckling, thinning.

Text-recognition to identify characters:
Pattern matching isolates characters (called glyphs) and compares with similar stored glyphs.
Only works with well scanned images typed in a known font.
Feature extraction converts glyphs into features and tried to find match among various stored glyphs. 

Post-processing - converts the extracted text data back into a computerized file or a TXT file.

CRNNs and LSTMs are neural network architectures that predict output at each time step.
RNN is a type of neural network where output from previous step is fed into the current step - designed to predict the next likely scenario. 

RNNs can keep track of arbitrary long-term dependencies but frequently encounters vanishing/exploding gradients.

LSTM adapt neural networks to partially solve this problem adding state to the layers.

Can be further adapted e.g. forget gates, peepholes, attention layers. 

# Advantages
Automates manual data entry processes.
Digital record keeping.
Automates checks such as automatic number plate recognition that can alert police to motoring offenses.
Reduce labour time.
Data accessibility.
Speeds up logistics such as passport verification. 

# Caveats
Struggles with blur and movement.
Cumbersome to train own model.
Often further post processing of text is required.

# Cloud
All major providers offer OCR.
Allow you to use prebuilt models.
They use key value pair extraction. 
Azure allows you to customize the model.
GCP has many pre-trained models for various industries. 
You can use Tesseract.

# Regex
You can use regex to improve the output. 