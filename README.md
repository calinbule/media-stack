## MEDIA STACK


1) clone this repo

```bash
git clone https://github.com/calinbule/media-stack.git .
```

2) rename the evv.sample file to .env then follow the instructions inside the file to define the necessary variables 

```bash
mv env.sample .env
```

3) set the executable flag on the install-media file

```bash
chmod +x install-media
```

4) run the install-media file to create the directory structure and create the docker cluster; this utility ca also be used to update the cluster if needed

```bash
./install-media
```
