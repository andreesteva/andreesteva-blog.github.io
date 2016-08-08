---
layout: post
title:  "How to switch into computer science and artificial intelligence"
date:   2016-08-05
categories: jekyll update
---

About 2.5 years ago I found myself at a crossroads in my PhD program,
and decided to switch fields from materials science research
(nanophotonics and plasmonics) to computer science research (artificial
intelligence). I was captivated by the broad impact that areas like
AI could have, the entire world was (and still is) getting on mobile
phones, and I felt like my work would leave a larger dent. This was a
huge challenge - I'm an electrical engineering PhD student and
essentially went from hardware to software search - which involved many learning curves.

I'm compiling below a condensed set of basic skills that helped me in my
transition, in the hope that those of you that are interested in such a
field switch might find it useful. This is very much a work in progress
and I welcome all comments and helpful suggestions! This post is
tailored slightly towards those interested in machine learning and
artificial intelligence, but may be useful for those thinking to other
areas of CS.

# General Topics:

1.  What hardware to use
2.  Working with Linux and Unix-based operating systems
3.  Command-line environments
4.  Text Editors
4.  Programming Languages for machine learning research
4.  Useful frameworks and codebases
5.  Basic knowledge of computer science
6.  Advanced Topics in Machine Learning and AI


------

# 1. What hardware to use

<strong>Desktops</strong>.
If you’re a researcher you’ll need a solid linux box complete with at least one machine-learning grade NVIDIA-GPU. I recommend System76 - their desktops are custom built, high-quality, and relatively cheap compared to larger companies. I use the Leopard Workstation. The Silverback Workstation is great too.

<strong>Laptops</strong>.
Use a MacBook Pro or a Linux laptop. Avoid Windows at all costs. While most of your develop and research will be on the desktop, its great to be able to ssh in remotely (ssh == secure shell: it lets you remotely enter a computer or server to get work done) and go work from the beach. Additionally, having a Mac is useful if you ever decide to build iOS apps.

<strong>GPUs</strong>.
This is where your machine learning and deep learning code will be trained and run. NVIDIA GPUs are essentially miniature supercomputers - they can have upwards of 3,000 cuda-cores, which serve to parallelize the massive computational demands of training a deep learning algorithm. When researchers figured out how to train a neural network on a GPU, train time went from months to days, and the deep learning explosion of 2012 occurred when a GPU-trained neural network won the ImageNet challenge.

------

# 2. Working with Linux and Unix-based operating systems

Linux is an amazing operating system that makes so many things easier for developers than Windows or Mac. Mac has a Unix kernel (Linux is Linus Pauling’s operating system built around a unix kernel) so it is still useful for development, but doesn’t have the stream-line workflow of Linux. Ubuntu is the most popular linux OS, its free, and I highly recommend it, as it is very user friendly. Also, Linux OS are free (minus Redhat’s enterprise distribution), and linux machines are cheaper than Windows and Mac. The catch is there’s a learning curve to working with Linux, but once you’re past it you’ll love Linux. I tolerate my Mac only because it has a Unix kernel.

Get acquainted with [StackOverflow](http://stackoverflow.com/), as it’ll be your best friend when debugging why things aren’t working. If anything throws an error, either while installing a program or running one, just paste the error into Google and look for the stack overflow post - I bet you someone has previously had the same issue.

Learn to use apt-get to install packages. Read up on package repositories and how installation works. Learn about makefiles and make, as you might be compiling your own code.

------

# 3. Command-line environments

Become familiar with navigating the filesystem: from moving around directories, to creating them, etc.

```
cd    # change directory
ls    # list what’s in a directory
mv    # rename or move a file
cp    # copy a file
man   # show the manual for a command
...
```

Here are the top 20 commands I use:

```
     1    1138  11.3811%   vim
     2    1096  10.9611%   l
     3    955   9.55096%   cd
     4    941   9.41094%   cat
     5    701   7.0107%    mv
     6    581   5.81058%   cp
     7    518   5.18052%   rm
     8    407   4.07041%   git
     9    367   3.67037%   mkdir
    10    320   3.20032%   grep
    11    263   2.63026%   find
    12    248   2.48025%   python
    13    177   1.77018%   ls
    14    155   1.55016%   head
    15    139   1.39014%   screen
    16    102   1.0201%    diff
    17    99    0.990099%  sudo
    18    85    0.850085%  nautilus
    19    75    0.750075%  py
    20    60    0.60006%   which
```

To see yours, type:

```bash
history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl |  head -n20
```

Of particular usefulness I think are: `grep`, `sed`, `find`, and `py`.

 - `grep`: used to search files for particular strings (sequences of characters)
 - `sed`: a utility that parses and transforms text
 - `find`: a utility that helps you find files and directories from partial strings
 - `py`: a utility that lets you evaluate python commands directly on the command line. Shout out to [Russell Stewart](https://github.com/Russell91/pythonpy) for putting this together.


------

# 4. Text Editors

You’ll be doing a lot of text-file editing - everything from writing source code to blogs ( 😃 ) includes text files. Notable editors are [vim](http://www.vim.org/), [emacs](https://www.gnu.org/software/emacs/), and [sublime](https://www.sublimetext.com/). Vim and emacs are command-line editors that open up directly in the terminal:

<center>
<img src="/assets/vim.jpg" width="50%"><br>
vim text editor
<br>
</center>

Sublime, on the other hand, is a rich-text editor that opens external to
the command line.

<center>
<img src="/assets/sublime.jpg" width="50%"><br>
sublime text editor
<br>
</center>

Which you choose is largely a question of personal taste. Personally I
find vim to be the best one, as I find that the keyboard shortcuts it
uses are more intuitive and easier to navigate than emacs, and
the fact that you don’t need the mouse at all makes it superior to
sublime. Additionally, the convenience of navigating the filesystem and
opening up text files all from a terminal makes it easier to use than
sublime.

Regardless, be sure to set up a configuration for it (to get the pretty
color coding you see in the pictures above). For vim, I use the
[janus](https://github.com/carlhuda/janus) distribution.
It has a plethora of wonderful plugins that make it simpler to navigate.

Here are a couple vim tutorials to consider (there is a learning curve):
<br>
[http://www.openvim.com](/http://www.openvim.com/) <br>
[https://danielmiessler.com/study/vim/](https://danielmiessler.com/study/vim/)

------

# 5. Programming Languages for machine learning research

<strong>[Python](https://www.python.org/)</strong>.
This is the most popular language for machine learning and AI research. It has a number of valuable modules for numerical operations, including numpy (Numerical Python), and scipy (Scientific Python) that allow you to work very efficiently with large matrices. You can usually do in a single line of python what would otherwise require a long function in other languages. I’m a fan of the [anaconda](https://www.continuum.io/downloads) distribution of python, as it includes almost everything you’d need.


<strong>[MATLAB](http://www.mathworks.com/products/matlab/?requestedDomain=www.mathworks.com)</strong>.
Though bulky, MATLAB is a decent language to use for rapid prototyping and analysis. It has many useful built-in packages for numerical processing. The downside is that MATLAB isn’t a real programming language, its very memory intensive, and you have to pay for it (though academic / student licenses are pretty cheap).


<strong>[C++](https://en.wikipedia.org/wiki/C%2B%2B)</strong>.
Widely used in industry for production code, C++ is very efficient and flexible, and great for large-scale systems. Python packages like numpy often create (under the hood) bindings for fast C++ functions. While C++ is a bit cumbersome for the rapid and hacky prototyping of research, its great for translating that code to enterprise-grade quality.


<strong>[Bash
Scripting](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)</strong>.
Learn to use this as it can save you a lot time manipulating files/folders/etc. Bash scripting is useful for running complex instructions with your filesystem.


<strong>[HTML](http://www.w3schools.com/html/html_intro.asp)</strong>.
In my opinion, every good AI researcher, back-end developer, and algorithms specialist should learn at least a bit of HTML. In AI research we often use crowdsourcing tools like Amazon Mechanical Turk to parse our datasets, and you have to build web GUIs for this.

------

# 6. Useful frameworks and codebases

<strong>Git</strong>.
Learn to develop code in a
[git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
workflow and integrate it with
[Github](github.com).

```bash
mkdir my-first-git-codebase
cd my-first-git-codebase
git init
echo “Explanation goes here” > Readme.md
git add .
git commit -am “Initial Commit"
```

And voila. Your first git repository is initialized. You can then push
code to github for remote storage: `git push -u origin master`.
Another reason I like the oh-my-zsh config is because any time you’re
in a git repo it’ll display the branch that you’re on (in this case,
master):

<center>
<img src="/assets/git.jpg" width="50%"><br>
git setup with branch displayed at command prompt.
<br>
</center>

<strong>Virtual Environments</strong>.
For python, its very useful to create virtual environments where you can
install dependencies that don’t conflict with system-wide installations,
and install these dependencies with versions specified all from a
requirements.txt file:

```bash
virtualenv .env
source .env/bin/activate
pip install -r requirements.txt
# [write some code]
deactivate
```

You may find yourself writing code that depends on prior versions of
python packages, or going back to code that you wrote some time ago.
Virtual environments preserve dependency versions to prevent updates
from preventing your code from working. For instance, in python 2 print
statements look like:
`python ‘Hello World!'`
and in python 3
`python(‘Hello World!’)`

<strong>Flask</strong>.
When it comes to web dev and HTML, its hard to beat flask. Its a python
micro-framework for web development that includes wrappers around SQL
databases. Its super easy to set up and work with. I’ve used it for
Amazon Mechanical Turk setups, for web interfaces to test algorithms
against medical practitioners, and to deploy object recognition models
on web sites.

<strong>Deep Learning Frameworks</strong>.
There are many good machine learning and deep learning
frameworks. I’ve worked closely both with Caffe and Tensorflow. Each
has their pros and cons. Tensorflow - released
earlier this year - is my personal favorite. Its a very flexible
framework capable of doing much more than just deep learning, and it
translated very easily from research code to production. Essentially the
same code that runs on a GPU will run on a CPU, a mobile device, in the
cloud, etc. The Google Cloud setup includes a tensorflow interface. The
website includes an extensive API and documentation, including simple
tutorials on how to put tensorflow code into scalable serving
environments in the cloud. Its written in python, and I expect it to
have the best support - both from Google and the developer community -
moving forth.

 * [Tensorflow (Google)](http://www.tensorflow.org)
 * [Torch (Facebook)](http://www.torch.ch)
 * [Neon (Nirvana)](https://github.com/NervanaSystems/neon)
 * [Caffe (UC Berkeley)](http://caffe.berkeleyvision.org/)

------

# 7. Basic knowledge of computer science

There's a reason universities offer computer science as its own major -
there are many interesting topics out there and the field has been
around for decades. Below are a few good courses offered by Stanford,
all of which have course notes online. Take a look at the topics offered
in each - typically homework assignments and examples are offered for
them.

 * [CS 106A](https://web.stanford.edu/class/cs106a/): Programming Methodology (Java)
 * [CS 106B](https://web.stanford.edu/class/cs106b/): Programming Abstractions
 * [CS 110](http://web.stanford.edu/class/cs110/spring-2016/): Principles of Computer Systems

------

# 8. Advanced topics in artificial intelligence

Here are some advanced foundational courses - not for the faint of
heart. Most course notes are offered for free, online, by Stanford,
including homework assignments.

 * [CS 229](http://cs229.stanford.edu/): Machine Learning
 * [CS 231n](http://cs231n.stanford.edu/): Convolutional Neural Networks
 * [CS 224d](http://cs224d.stanford.edu/): Deep Learning for Natural Language Processing
 * [CS 221](http://web.stanford.edu/class/cs221/): Artificial Intelligence
 * [EE 364a](http://stanford.edu/class/ee364a/): Convex Optimization
 * [CS 228](http://cs.stanford.edu/~ermon/cs228/index.html): Probabilistic Graphical Models
 * [Linear Algebra Review](http://cs229.stanford.edu/section/cs229-linalg.pdf)
 * Vector Calculus

 ------

# 9. Further resources

 <strong>Computer Vision Conferences</strong>

 * Computer Vision and Pattern
 Recognition ([CVPR](http://cvpr2016.thecvf.com/))
 * European Conference on Computer Vision
 ([ECCV](http://www.eccv2016.org/))
 * International Conference on Computer Vision
 ([ICCV](http://pamitc.org/iccv15/))

 <strong>Machine Learning and General AI Conferences</strong>

 * International Conference on Machine Learning
 ([ICML](http://icml.cc/2016/))
 * Neural Information Processing Systems ([NIPS](https://nips.cc/))
 * Association for the Advancement of Artificial Intelligence
 ([AAAI](http://www.aaai.org/home.html))

 {% include disqus.html %}
