#### dockerfile-newsbeuter

`newsbeuter` is the `mutt` of rss feed readers. http://www.newsbeuter.org/

#### Initial setup

```
mkdir ~/newsbeuter-conf
#
# poor permissions needed so that the cache can be written out by the docker user
chmod 777 ~/newsbeuter-conf
#
# create basic subscriptions and config
cd ~/newsbeuter-conf
echo "http://newsbeuter.wordpress.com/feed/" > urls
echo "auto-reload yes" > config
echo "refresh-on-startup yes" >> config
#
# build docker container, only if you don't want to run from the Docker hub:
docker build -t newsbeuter .
```

#### Routine use:
```
cd ~/newsbeuter-conf
docker run -it --rm=true -v `pwd`:/home/rss/.newsbeuter:rw schvin/newsbeuter
```
