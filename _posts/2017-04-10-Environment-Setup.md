---
title: Environment Setup
layout: post
permalink: /environment-setup/
source-id: 1xxzBKH0Xsz0cdo8aWTvHNlrzrnxzoac63V6qLZJ_rqE
published: true
---
# Goals

* We should have a [Github repo](https://github.com/no-fire/line-follower)

Each person should be able to...

* Run the code from last project on their laptop

* Access DeepThought and/or Nathan's Beast and run intensive network training code

* Access and contribute to [whatever the training data repository is]

# Instructions

## Things to install

* Python 2.7

    * Test: in terminal, run `python --version`

* ML Libraries:

    * [TensorFlow](https://www.tensorflow.org/install/)

        * Don't try to set up GPU support, it will end in fire and pain.

        * `sudo -H pip install tensorflow`

        * Test: in terminal, run `python -c "import tensorflow; print('Works!')"`

    * [Keras](https://keras.io/#installation)

        * `sudo -H pip install keras`

        * Test: in terminal, run `python -c "import keras"` It should say "Using TensorFlow backend."

* ROS Kinetic

    * Test by running `rosversion -d` in a terminal

* Misc

    * [Bcolz](http://bcolz.readthedocs.io/en/latest/install.html)

        * Test: run `python -c "import bcolz; bcolz.test()"`

    * [Numpy](https://scipy.org/install.html): The preferred way to run numeric computations in python. All hail Numpy.

        * Test: run `python -c "import numpy as np; np.test()"`

    * [Glob](https://pypi.python.org/pypi/glob2): Returns names of items in a directory as a list.

        * Test: run `python -c "from glob import glob; print('Works')"`

    * PIL

    * [Matplotlib](https://matplotlib.org/users/installing.html): Plots in python, based off of MatLab's plvotting commands

        * `sudo apt-get install python-matplotlib` for Ubuntu Linux

        * Test: run `python -c "import matplotlib.pyplot as plt; print('Works!')"`

    * [Seaborn](http://seaborn.pydata.org/installing.html): Prettier plots on top of matplotlib

        * Test: `python -c "import seaborn as sns;print('Works')"`

    * [Tqdm](https://pypi.python.org/pypi/tqdm#installation): Adds progress bars to loops

        * Test: `python -c "import tqdm; print('Works')"`

## Connecting to Nathan's computer:

Put your SSH public key here:

<table>
  <tr>
    <td>ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCdEy6qrhnNjqSlbYngjM9m63OvHMiZvxMeNOqLJCJvopDPI0w6ozfKTHwrchqcfY/4pAa9MvSnEOS0hXF6t7oMSFk1psQlgLHxigXbG66SqAeT1pHAkhe91F2HGafNurazbBj5ejQZNqw8ch24aCPGKF/KxcmZbQXNZ7RcNwu5ex8Ke5TqpHUpbqNrq23rrqQz8gnEXvUZTM31eIWAgSIjCbJUpyCqSelBnD7c/NUW/Eo+i18Hgt3fcPk9xMq+U92E5D3ljUfV5PIYJmvwVmslFvqsqWQ2+OvnoI6ey/mSXyEMDwV2cd/oPOxtTAebOT23wK0CYXoKi9K9QSzUmyvKDFaw48+fa6ekJKc8/6rRGCZf26t7FCa+XkoltvBDAF06vhXAF3pIuXjhsQA1vb3aNUe9TBuBbuBrilbXnHwFeyJdExt7i5eaYnqY/TjnMKGiluKRNXoH8BCVjJGUJkarn4gI+ptsRkZRVekDegR/aamFDeKt4hasNtjCROK1CfdMCxpUU09ZT2+KJy2wU5UYsJXfq0J0SrIlqLpNqqihhG6EzVnsw4LaTHBKlRP6YcM1ZdSCG3jQTr2nJj5reU66RUmf/LNoP4mI47Kb2kGSRTPfF/HyirgaPYwolIfMY3ZzI0dthkC9x0jtxDABN0UHiGae4E5jAZ1htSize3PclQ== eric@legoaces.org</td>
  </tr>
  <tr>
    <td>ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDkwimd7GWBFmJsBrxijEulSZjb0pJqcbIfU4S7ajH0fnU8491J6EQFOAjKrnvhq7jTu+B/TmbEl0xeY02+BEp+0mANOkDqUtM1gf4re3bFwT9SNYA2wmCjPJvOKSQrngOUn/858jd8cGCxRngC4loEvVfoUHan7mxnQntU22rnlKZnQjRdRr3FWhv0T9rx1OUeenjUX7RBkyIdEMZQIMel+r7PI8Jw/q23fh0pij4qembZJVu2rSF0xxW879R9UTD83Y3FWNklHb/qlssEAotcKGNBTyUGezmasVkXpAFpDQ4mUObR7b9KYr/Eljz7HpUQkPZPrtso1vzU/+hfAoZ9WKHI7eJFM+7pItcn9QxPLn5O9kou/+4CILJlLUoeWl52Sf0Ki05X6aJcj/KTXOS0jPUeD9fB2+SEP+qVgH61zF/kyluNwNot6Y2XVPJIIlJxBie1GxUA4ka5R6g34K/hhBBm8REk6B6BU0ZfCxV1eIOrH3UCLF5/kugncSHRF3bHp5MM1CQ80LFXZhxG5MrwQ4X/tPgmYJSIF8qVYsrfnS+gvH7KI7JSI8MscwPgN6McP3GnaXnyLuI23CvSWHzGqmqtM9BDGNVwDWLThMz/6fCLgi9FOClr9xAJ5NWpoS79JLWcESUHvOfoGbN0PPlbr7k8I9mlc9fErQdxEFy0FQ== lauren.gulland@students.olin.edu</td>
  </tr>
  <tr>
    <td>Nathan Laptop
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDMtM97hHsEscozL6smXReZF3r6Vsq5CAyDm2OmsMNls3I8goIwU1JWKxpZhhcKyTNbdlqhgqMHcAAKtM8X4qfawJbNKqh9027LgZeFF47tpre2kXzdQWUZOfifx65ADfYA5CEXpR+oIvYFf0zkQL8XdegOAZyg1KvmlEXSVf1QYC3TDV0b3nNI8qZccvcj7nNWrvhrZI5K+2boPQtoVLSPrVmdxSVcTnAYKa74JK8OSG0QT9BRThFv699Wzj/Hm9iwAQtv9nR8qXTjBE/wkkCw8MaVZzNuvRY8e51fDg6Y7V1MgPdiif5CN/abD48QIPr6syWyTeiCjVi9XeArfFYC+/hB88B96/Kzac/M0VxPiggqtd20YsB5N4F+A5amNNaXnlL/fmawvZy0ifyZZCIOnYAm04W6bPK57It5v9BkQPR+gKy8TEYNZ9eVaZwsQn2V1JH3x4InUNsRBP6WstklaCzj5piAJrM+IZbykfvUgKJBQOPtc9nlRQafasfO1fxqrQ/1TTQC63r+zhi+RPZ5vZvgB5eCPVPW52jMuFTARoAftTPBM1uApmlbmkgfd7cmS4EPcTlk7oYAVyVkMWMavBaIBwBbPwpk75YQLpBIABTtJMZyhnq5DLZ7QzRZaVsbfhfLFEnLznyXBeS7Wz9uKcXjYG7r2zq++9T2wzYWWQ== nathaniel.yee@students.olin.edu</td>
  </tr>
</table>


Once Nathan authorizes access...

* Want a terminal

    * `ssh nathan@nathanDesktop`

    * `tmux ls`

        * Should print out that jupyter_server is running.

    * `tmux a -t jupyter_server`

        * Navigate tmux using ctrl+b, arrow key

        * [https://learnxinyminutes.com/docs/tmux/](https://learnxinyminutes.com/docs/tmux/)

        * [https://danielmiessler.com/study/tmux/#gs.=j=4xnE](https://danielmiessler.com/study/tmux/#gs.=j=4xnE)

* Want to use remote jupyter browser in your browser

    * `ssh -N -f -L localhost:8890:localhost:8890 nathan@nathanDesktop`

    * Go to localhost:8890/tree in browser

    * Change kernel to 'Python [condaenv:deepLearning]'

* Want a file explorer - nautilus

    * sftp://nathan@nathandesktop/home/nathan/olin/spring2017/line-follower

* Broadcast a message

    * `wall _____`

## Code to download

Clone our repository into 

