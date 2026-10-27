---
published: true
title: How to use news2kindle
category: productivity
tags: rss kindle reddit google-news news2kindle
---

## Background

I want to browse Reddit posts and Google News with my Kindle oasis, so that I don't get distracted too much and easier for my eyes.

## Tools selection

With some Google search, I mainly found 3 tools:

- [Feeder](https://www.feeder.mobi/)
- [news2kindle](https://github.com/anteprandium/news2kindle)
- [kindlepush](https://github.com/zhengchun/kindlepush)

I tried Feeder and immediately found it's broken, so pass. Finally I chose to go with news2kindle.

### Why choose news2kindle over kindlepush?

news2kindle is only a simple python script, so it's universally accessible, while KindlePush only supports Windows and Linux. I noticed KindlePush is made by Chinese, so will keep as a send option.

## How to run news2kindle locally

### Prerequsite

- Docker (run with container) or Python (run locally)

### Installation

```sh
docker build -t news2kindle .
```

### Configuration

1. Add RSS to feeds.txt (note: The modification date of `feeds.txt` will be the starting date from which news are downloaded.)

2. Enable IMAP in Gmail settings

3. Get an app password for Gmail

4. Test SMTP configuration https://www.gmass.co/smtp-test

5. Config environment variables with a `.env` file in project root folder as such:

```
EMAIL_SMTP=smtp.gmail.com
EMAIL_SMTP_PORT=465
EMAIL_USER=[your gmail address]
EMAIL_PASSWORD=[your gmail app password]
EMAIL_FROM=[your gmail address]
KINDLE_EMAIL=[your kindle device address (remember to add your send email to Amazon trust emails.)]
```

### Run

```sh
docker run --env-file .env news2kindle
```

## How to run news2kindle on heroku

### Prerequsite

- Heroku CLI

### Steps

1. create a heroku app
1. set stack to container  
   `heroku stack:set container --app app_name`
1. config environment variables in Config Vars
1. deploy code or docker image to heroku (see: 3 ways to deploy to heroku)
1. scale up the worker dyno  
   `heroku ps:scale worker=1`

### 3 ways to deploy to heroku

1. Heroku Git. Push code to heroku repo.
1. GitHub. Automatic deploys triggered by code push to Github repo
1. Container Registry. Build the Dockerfile locally and push the Docker image to heroku.

### Build Docker images on Heroku

To build Docker images on Heroku, instead of building the image locally, you can specify that with a heroku.yml file.

```yml
build:
  docker:
    worker: Dockerfile
```

### Use Heroku Scheduler to trigger news2kindle

The original news2kindle will run forever. To make the worker process more effective, I decided to make it run on schedule.

To achieve this, I did the following:

1. Modify the `src/news2kindle.py` to only [do one around](https://github.com/goooooouwa/news2kindle/commit/e7b009ad48a688769ed5676a02a547c5b079f3bb) per invocation
1. Install the [Heroku Scheduler](https://devcenter.heroku.com/articles/scheduler) addon
1. Add a job to run command `python3 src/news2kindle.py` on a daily schedule

- run it on heorku scheduler
- start a python http server as web dyno

### Developing news2kindle

- add heroku.yml to build image on heroku
- modify the `src/news2kindle.py` to only do one around
- display local time
  - add timezone environment variable
  - display post & start time as timezone
- remove conver image.
- change title to show start time.

### Troubleshooting

#### Issue: feeds list not updated

Since the config is copied to the image when build, if you edit the feeds.txt or anything in the `config` folder, you need to rebuild the image.

#### Error type: environment value is not set correctly

Error message:

```python
File "/usr/local/lib/python3.8/smtplib.py", line 645, in auth
    authobject(challenge).encode('ascii'), eol='')
AttributeError: 'NoneType' object has no attribute 'encode'
```

Example root cause: email password environment spelled wrong, should be `EMAIL_PASSWORD`, I used `EMAIL_PASSWD` from the code instead.

#### Error type: SSL port is incorrect

Error message:

```python
File "/usr/local/lib/python3.8/ssl.py", line 1309, in do_handshake
    self._sslobj.do_handshake()
ssl.SSLError: [SSL: WRONG_VERSION_NUMBER] wrong version number (_ssl.c:1125)
```

Example root cause: SSL port for Gmail SMTP is `465`, don't put `25` or `587`, etc.

#### No log of worker in Heroku

Root cause: worker dyno is not running.

By default your free dyno worker is off. Like this:

![]({{site.baseurl}}/assets/images/cfG11FS.png)

You need to manually scale up the worker dyno to let the process actually run!

Make sure the worker dyno is on:

![]({{site.baseurl}}/assets/images/vr1HpVc.png)

Then you can see the worker is running and generating logs.

![]({{site.baseurl}}/assets/images/eFlT8s5.png)

### Heroku Scheduler not running

Root cause: it's actually run, just not on time. It will probably be delayed several minutes. So have a bit patience.

Accoridng to the [doc](https://devcenter.heroku.com/articles/scheduler#known-issues-and-alternatives):

> Scheduler is a free add-on with no guarantee that jobs will execute at their scheduled time, or at all:
>
> - In very rare instances, a job may be skipped.
> - In very rare instances, a job may run twice.

Take a look at the log shown below. Notice the time of the scheduler start and actual worker run.

![]({{site.baseurl}}/assets/images/Gb18CrL.png)

## Next steps

1. [ ] Fine tune RSS feeds for blogs, Google News, Reddit.
2. [ ] fetch full article for each Google News rss feed or setup shadowsocks proxy for kindle
3. [x] runs it up on a server
4. [x] display local time
5. [x] cover with date
