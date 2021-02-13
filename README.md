# Docker-Qt
C++ Qt compile environment for Docker (Dynamically Linked, Statically Linked, and Cross-compiled to Windows)

* Linux Dynamically Linked
```
docker build --force-rm -f Dockerfile -t fffaraz/qt:latest .
docker run --rm -it -v $(pwd):/app fffaraz/qt:latest /bin/bash
```

* Linux Statically Linked
```
docker build --force-rm -f Dockerfile.static -t fffaraz/qt:static .
docker run --rm -it -v $(pwd):/app fffaraz/qt:static
```

* Windows 64bit Cross-compiled Statically Linked
```
docker build --force-rm -f Dockerfile.win64s -t fffaraz/qt:win64s .
docker run --rm -it -v $(pwd):/app fffaraz/qt:win64s
cd /app
qmake
make -j $(nproc)
```

## Creating Docker Packages

Linux Static:

```bash
# build linux image (takes about 20 minutes)
docker build --force-rm -f Dockerfile.static -t fffaraz/qt:static .

# push to github container registry
# run using git bash
docker tag fffaraz/qt:static docker.pkg.github.com/nathanesau/docker-qt/qt-static:1.0
docker push docker.pkg.github.com/nathanesau/docker-qt/qt-static:1.0
```

Windows 64 Static:

```bash
# build windows 64 image (takes about 20 minutes)
docker build --force-rm -f Dockerfile.win64s -t fffaraz/qt:win64s .

# push to github container registry
# run using git bash
docker tag fffaraz/qt:win64s docker.pkg.github.com/nathanesau/docker-qt/qt-win64s:1.0
docker push docker.pkg.github.com/nathanesau/docker-qt/qt-win64s:1.0
```
