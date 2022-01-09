# deepstack manager

Simple command-line tool to manage faces "memory" of deepstack instance. It provides simple means to register, delete and list faces as well as submit images for face recognition or object detection. 

The script simplifies registering face with multiple images by submitting all image files present in current directory.  

NOTE: If recieving 500 errors at registration, you might be low on RAM. 4GiB is probably a minimum even for just a few faces/pictures

<pre>

$ dsm -h
usage: dsm [-h] [-H HOST] [-K API_KEY] {register,recognize,detect,delete,list} ...

Deepstack management tool.

positional arguments:
  {register,recognize,detect,delete,list}

optional arguments:
  -h, --help                    show this help message and exit
  -H HOST, --host HOST          Address of deepstack server
  -K API_KEY, --api_key API_KEY API-key for deepstack server



$ dsm register -h
usage: dsm register [-h] [-m MASK | -p PATH] name

positional arguments:
  name                  Name to register

optional arguments:
  -h, --help            show this help message and exit
  -m MASK, --mask MASK  Mask for files to include
  -p PATH, --path PATH  Path



$ dsm recognize -h
usage: dsm recognize [-h] file

positional arguments:
  file        File to submit for face recognition



$ dsm detect -h
usage: dsm detect [-h] file

positional arguments:
  file        File to submit for object detection



$ dsm delete -h
usage: dsm delete [-h] name

positional arguments:
  name        Name to delete

Examples:
---------
Register all .jpg-files in the folder svenotto-faces with the name svenotto
$ ./dsm.py -H 192.168.6.167 -K someverysecretkey register -p ../f
ace/svenotto-faces/ svenotto

Perform face recognition on one picture
$ ./dsm.py -H 192.168.6.167 -K someverysecretkey recognize ../testfaces/svenotto/svenotto_jumping101.jpg