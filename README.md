# MusicalMotifMaker
Use a GAN to create music with motifs. Our goal was to create music that had repeated motifs in the piece. 

## Idea
We wanted to learn how to apply a generative adversarial network to create images. After finding success with the MNIST Fashion dataset <insert image>, we wanted to see what else we could apply this technique to. 
  
We were previously interested in using neural networks to create music, but had no experience with Recurrent Neural Networks which are typically used to create time-series information such as music. 

Our idea was that instead of using a RNN, we could encode time across the space of an image and let the convolution encode that information to generate music that featured repeating patterns. This way, the GAN would generate the entire song at once while hopefully learning to create repeating patterns across the piece.

## Data Preparation Pipeline
Song (MIDI) -> Extract Melody from Song (MIDI) -> Encode Song into Image (PNG)
#### Melody Extraction
To simplify the images and keep them in grayscale, we wanted to only encode the melody of the piece. 
<insert explanation and sample>
  
#### Song Encoding
To encode the song into an image, we found the smallest time note of the song and sampled the song at the interval. Each sampling produced a pixel in our 28x28 image. The pixels were filled starting at the top left, going to the end of the row before starting the next. The pixel intensity was directly proportional to the sample's pitch, a lower pitch corresponded to darker color and a higher pitch corresponded to a lighter color. A rest was encoded as white (255).

## Post Generation Processing
To make the generated piece sound better, we tried to normalize it to a single scale. 
<insert explanation and sample>

## For the Future
There are many things we would like to try for the future.

#### Improved melody extraction
Our melody extraction algorithm did a poor job of extracting the melody which made our training data near unusable. We would like to implement Justin Salamon's [Melody Extraction](http://www.justinsalamon.com/melody-extraction.html) to improve the quality of our training data.
<insert other improvements>

