1. Create a virtual environment using `venv`:
```py
python -m venv ./venv
```

This creates a new folder in the directory where you are working. You can name the `./venv` portion of this command anything you want. The `./` indicates your path and can be set up any way you like. The `venv` portion is the name of your folder and can be any name you choose.

2. To activate your `venv` environment, you type
```
source /root/venv/bin/activate
```
`source` is the command that points to the file. WHat follows is the path to the `activate` command in your `bin` file. `venv` is the name of the folder that you created in the previous step.

3. Once your environment is activated, you can operate as you like within your virtual environment. 

4. When you want to deactivate your virtual environment, type
```
deactivate
```

Your computer will return you to your default shell (bash, zsh, etc.)
