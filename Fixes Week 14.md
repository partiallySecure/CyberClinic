# Fixes Week 14

fix for pip install problem on uni VMs:

```jsx
git clone https://github.com/CravateRouge/bloodyAD
cd bloodyAD
python3 -m pip install . --trusted-host=pypi.python.org --trusted-host=pypi.org --trusted-host=files.pythonhosted.org 
```

```jsx
python3 -m pip install . --trusted-host=pypi.python.org --trusted-host=pypi.org --trusted-host=files.pythonhosted.org 
```