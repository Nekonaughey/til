TL;DR;
bitbucket pipelinesを使っていて、毎回手動でパイプラインを実行していた。
pushトリガにする方法を調べた。


参考資料
https://ja.confluence.atlassian.com/bitbucket/configure-bitbucket-pipelines-yml-792298910.html


現状
以下の感じでcustomになっていた。
ドキュメントに以下の記述がある。
custom - Bitbucket Cloud インターフェイスから手動またはスケジュール実行でのみトリガーできるパイプラインを定義します

image: atlassian/pipelines-awscli
pipelines:
  custom:
    deploy:
      - variables:
          - name: Version
      - step:
          name: web
          deployment: test
          services:
            - docker
          caches:
            - docker
          script:

対応
以下の感じで、customではなくて、brancesを使う。

image: atlassian/pipelines-awscli
pipelines:
  branches:
    master:
      - step:
          name: Clone
          script:
            - echo "Clone all the things!
