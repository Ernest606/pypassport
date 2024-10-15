THIS PROJECT IS MODIFIED VERSION OF THIS GITHUB REPOSITORY: https://github.com/roeften/pypassport

## Entrypoint to install pypassport:
1. Update your package lists:
    ```bash
    sudo apt-get update
    ```
2. Install the necessary dependencies:
    ```bash
    sudo apt-get install libpcsclite-dev pcscd
    ```
3. Navigate to the `pypassport` directory:
    ```bash
    cd pypassport
    ```
4. Install the `pypassport` package:
    ```bash
    pip install .
    ```


# pypassport
pypassport for python3

Tested working so far:

```
from pypassport.reader import ReaderManager
from pypassport.epassport import EPassport, mrz
r = ReaderManager()
reader = r.waitForCard()
p = EPassport(reader,"YOURMRZINFO")
p.register(print)
p.setCSCADirectory("C:\\TEMP")
p.doBasicAccessControl()
p.doActiveAuthentication()

p['DG2']

```

The picture can be read and saved as well:

```
....

import io
from PIL import Image

passportimage = p['DG2']['A1']['5F2E']
imgfp = io.BytesIO(passportimage)
img = Image.open(imgfp)
img.save("c:\\TEMP\\passport.png")

```
If you find any conversion issues pls let me know.
