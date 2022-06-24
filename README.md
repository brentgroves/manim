# manim
# docker run -it --name my-manim-container -v "/home/bgroves@BUSCHE-CNC.COM/srcmanim:/manim" manimcommunity/manim /bin/bash
# docker run -it -p 8888:8888 manimcommunity/manim jupyter lab --ip=0.0.0.0


June 24, 2022, Notes 

I set jupyterHub up with a docker file and I had to use ipython kernel to install a kernel for each conda environment, but when you use anaconda_navigator you do not need to install multiple kernels.  You only need to select the conda environment before launching jupyter notebooks. You also must include the %%manim directive with the class name before the class definition. 

https://docs.manim.community/en/stable/installation/linux.html 
sudo apt update 
sudo apt install libcairo2-dev libpango1.0-dev ffmpeg 
Install media codecs 
sudo apt install ubuntu-restricted-extras 
conda create -n manim python=3.10 
conda activate manim 
pip3 install manim 

from manim import * 

%%manim -qm -v WARNING SquareToCircle 
 
class SquareToCircle(Scene): 
   def construct(self): 
      square = Square() 
      circle = Circle() 
      circle.set_fill(PINK, opacity=0.5) 
      self.play(Create(square)) 
      self.play(Transform(square, circle)) 
      self.wait() 

 

%%manim -qm -v WARNING SquareAndCircle  

class SquareAndCircle(Scene): 

def construct(self): 

circle = Circle() # create a circle 

circle.set_fill(PINK, opacity=0.5) # set the color and transparency 

square = Square() # create a square 

square.set_fill(BLUE, opacity=0.5) # set the color and transparency 

square.next_to(circle, RIGHT, buff=0.5) # set the position 

self.play(Create(circle), Create(square)) # show the shapes on screen 

 
%%manim -qm -v WARNING AnimatedSquareToCircle 

class AnimatedSquareToCircle(Scene): 

def construct(self): 

circle = Circle() # create a circle 

square = Square() # create a square 

self.play(Create(square)) # show the square on screen 

self.play(square.animate.rotate(PI / 4)) # rotate the square 

self.play( 

ReplacementTransform(square, circle) 

) # transform the square into a circle 

self.play( 

circle.animate.set_fill(PINK, opacity=0.5) 

) # color the circle on screen 

 
