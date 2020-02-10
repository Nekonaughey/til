明らかにバグだと思われるが、以下のような２つのstepがあると、
docker imageをキャッシュしてくれるのは片方だけ。

キャッシュがクリアされるのは、２週間経過したタイミングが、手動でクリアしたときだけ。
https://community.atlassian.com/t5/Bitbucket-Pipelines-questions/Node-Cache-shouldn-t-persist-when-there-is-a-change-in/qaq-p/1089674


 deployWeb:
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
   

    deployServer:
      - variables:
          - name: Version
      - step:
          name: server
          deployment: test
          services:
            - docker
          caches:
            - docker
          script:
