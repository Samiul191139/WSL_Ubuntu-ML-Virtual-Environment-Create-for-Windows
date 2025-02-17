# WSL_Ubuntu-ML-Virtual-Environment-Create-for-Windows
WSL Ubuntu virtual Environment setup for Notebook to access local GPU

TensorFlow 2.10 was the last TensorFlow release that supported GPU on native-Windows. Starting with TensorFlow 2.11, you will need to install TensorFlow in WSL2. To Access local PC's gpu while running the latest Tensorflow, Python and other Py libraries, follow the following steps.

**Step 1:**
- Install WSL (Ubuntu for Windows - can be found in Windows Store). I recommend the latest version (I'm using 2.3)

**Step 2:**
- Go to https://repo.continuum.io/archive to find the list of Anaconda releases

**Step 3:**
- Select the release you want. I have a 64-bit computer, so I chose the latest release ending in `x86_64.sh`. If I had a 32-bit computer, I'd select the `x86.sh` version. If you accidentally try to install the wrong one, you'll get a warning in the terminal. I chose `Anaconda3-2024.06-1-Linux-x86_64.sh`.

**Step 4:**
- From the terminal run `wget https://repo.continuum.io/archive/[YOUR VERSION]`. Example: `$ wget https://repo.continuum.io/archive/Anaconda3-2024.06-1-Linux-x86_64.sh`

**Step 5:**
- Run the installation script: `$ bash Anaconda[YOUR VERSION].sh` (`$ bash Anaconda3-2024.06-1-Linux-x86_64.sh`)

**Step 6:**
- Read the license agreement and follow the prompts to accept. When asks you if you'd like the installer to prepend it to the path, say yes. Optionally install VS Code when prompted (some have reported this installation doesn't work - checkout https://gist.github.com/kauffmanes/5e74916617f9993bc3479f401dfec7da#gistcomment-3665550).

**Step 7:**
- Close the terminal and reopen it to reload .bash configs.

**Step 8:**
- To test that it worked, run `$ which python`. It should print a path that has anaconda in it. Mine is `/home/kauff/anaconda3/bin/python`. If it doesn't have anaconda in the path, do the next step. Otherwise, move to step 10.

**Step 9:**
- Manually add the Anaconda bin folder to your PATH. To do this, I added "export PATH=/home/kauff/anaconda3/bin:$PATH" to the bottom of my ~/.bashrc file.

**Step 10:**
- To open jupyter, type `$ jupyter notebook --no-browser`. The no browser flag will still run Jupyter on port 8888, but it won't pop it open automatically. it's necessary since you don't have a browser (probably) in your subsystem. In the terminal, it will give you a link to paste into your browser. If it worked, you should see your notebooks!

**Step 11:**
- If you want to run it on VSCODE: Open vscode, go to 'extensions', search 'WSL' and install it.

**Step 12:**
- Left down the corner of vscode, there should be an option to connect to live server. If there is none, install 'live server' extension. After installing, click on the button (left down side of vscode) and connect to WSL.

**Step 13:**
- Open 'wsl' and create an environment for WSL. use command
######
        conda create -n <environment name>

**Step 14:**
- At the upper right corner of your notebook, there is an option to choose kernel, choose the kernel you created in 'step13'.
- Activate the kernal
######
        conda activate <environment name>
        
-  install tensorflow and cuda
######
        python3 -m pip install tensorflow[and-cuda]
        
> [!IMPORTANT]
> Run this command to verify if the gpu is detected by the system.
######
        python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"

**Step 15:**
- Install other libraries as needed [if you want to install libraries in your environment, use vscode terminal while your desired kernel is activated.

Go to your IDE and test a code to verify it's working.

<p align="center">Happy Coding 🐞</p>

## Contact
GitHub [@Samiul191139](https://github.com/Samiul191139)
