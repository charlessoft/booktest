# Intro
----

项目路径：/data/BasinSpace/src/bidspy

- basin-textminer: 文本处理，语料库表达。内含多个小project，如招标公告提取
- annotator-server: 招标公告提取分析接口， annotator接口， crf训练接口等


# Deploy
----

## Create Virtualenv

...（可选）

## Install

    cd /home/yychen/basin/bidspy
    
    pip install basin-textminer/
    pip install -r annotator-server/requirements.txt
    
## Run

    python annotator-server/run.py

接口调用方式详见: annotator-server/README.md

# 集成
----

## run docker

docker run -d --name=bidspy -p 0.0.0.0:12000:5000 bidspy