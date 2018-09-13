# Google Colab Tutorial

Colab is a Google’s free cloud service which will let you run your deep learning or machine learning models in cloud.

### Creating New Colab Notebook

* Open your Google Drive
* Create a new notebook via Right click > More > Colaboratory

### GPU Setting

Edit > Notebook settings or Runtime>Change runtime type and select GPU as Hardware accelerator

### RAM Info
```
!cat /proc/meminfo
```

### CPU Setting

```
!cat /proc/cpuinfo
```

### Install Libraries

!pip install or !apt-get install

```
!pip3 install tensorflow==1.8
!pip3 install keras
!pip3 install torch torchvision
!apt-get install python-numpy python-scipy
```

### Cloning Github Repo to Google Colab

```
!git clone https://github.com/ildoonet/tf-pose-estimation.git
```
### Mount your Google Drive

```
!apt-get install -y -qq software-properties-common python-software-properties module-init-tools
!add-apt-repository -y ppa:alessandro-strada/ppa 2>&1 > /dev/null
!apt-get update -qq 2>&1 > /dev/null
!apt-get -y install -qq google-drive-ocamlfuse fuse

# Generate auth tokens for Colab
from google.colab import auth
auth.authenticate_user()
# Generate creds for the Drive FUSE library.
from oauth2client.client import GoogleCredentials
creds = GoogleCredentials.get_application_default()
import getpass
!google-drive-ocamlfuse -headless -id={creds.client_id} -secret={creds.client_secret} < /dev/null 2>&1 | grep URL
vcode = getpass.getpass()
!echo {vcode} | google-drive-ocamlfuse -headless -id={creds.client_id} -secret={creds.client_secret}
# Create a directory and mount Google Drive using that directory.
!mkdir -p Drive
!google-drive-ocamlfuse Drive
```

### Check your Folder Data

```
!ls Drive/test
```

### Upload code from your system

```
from google.colab import files
uploaded = files.upload()
```
### Make zip file of your Data

```
from google.colab import files
import zipfile
import sys
foldername = 'your folder or filename'
zipfile.ZipFile('Drive/'+foldername + '.zip', 'w', zipfile.ZIP_DEFLATED)
```

### Downloading the data from the colab

```
from google.colab import files
files.download('Drive/test.zip')
```
