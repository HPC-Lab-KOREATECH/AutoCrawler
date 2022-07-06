# AutoCrawler
Google, Naver multiprocess image crawler (High Quality & Speed & Customizable)

![](docs/animation.gif)

# How to use

1. Install Chrome

2. pip install -r requirements.txt

3. Write search keywords in keywords.txt

4. **Run "main.py"**

5. Files will be downloaded to 'download' directory.


# Arguments
usage:
```
python3 main.py [--skip true] [--threads 4] [--google true] [--naver true] [--full false] [--face false] [--no_gui auto] [--limit 0]
```

```
--skip true        Skips keyword if downloaded directory already exists. This is needed when re-downloading.

--threads 4        Number of threads to download.

--google true      Download from google.com (boolean)

--naver true       Download from naver.com (boolean)

--full false       Download full resolution image instead of thumbnails (slow)

--face false       Face search mode

--no_gui auto      No GUI mode. (headless mode) Acceleration for full_resolution mode, but unstable on thumbnail mode.
                   Default: "auto" - false if full=false, true if full=true
                   (can be used for docker linux system)
                   
--limit 0          Maximum count of images to download per site. (0: infinite)
--proxy-list ''    The comma separated proxy list like: "socks://127.0.0.1:1080,http://127.0.0.1:1081".
                   Every thread will randomly choose one from the list.
```


# Full Resolution Mode

You can download full resolution image of JPG, GIF, PNG files by specifying --full true

![](docs/full.gif)



# Data Imbalance Detection

Detects data imbalance based on number of files.

When crawling ends, the message show you what directory has under 50% of average files.

I recommend you to remove those directories and re-download.


# Remote crawling through SSH on your server

```
sudo apt-get install xvfb <- This is virtual display

sudo apt-get install screen <- This will allow you to close SSH terminal while running.

screen -S s1

Xvfb :99 -ac & DISPLAY=:99 python3 main.py
```

# add_params

 `add_params_google.txt`, `add_params_naver.txt`에 검색시 추가할 GET 매개변수 등록
 
구글 이미지 고급 검색 - http://images.google.com/advanced_image_search?hl=ko

네이버 이미지 검색 - https://search.naver.com/search.naver?where=image&sm=tab_jum&query=

## 주요 매개변수

네이버 `&res_fr=786432&res_to=100000000`

구글 `&tbs=isz:lt,islt:70mp`

# Customize

You can make your own crawler by changing collect_links.py

# Issues

As google site consistently changes, please make issues if it doesn't work.
