# download

\$ docker pull chaosbladeio/chaosblade-demo

# start

\$ docker run -it --privileged chaosbladeio/chaosblade-demo

# Эксперимент 1

1. curl http://localhost:8080/dubbo/hello?name=dubbo
2. blade prepare jvm --process business
3. blade create dubbo delay --time 3000 --service com.example.service.DemoService --methodname sayHello --consumer
4. curl http://localhost:8080/dubbo/hello?name=dubbo
5. blade destroy <UID>
6. curl http://localhost:8080/dubbo/hello?name=dubbo

# Эксперимент 2

1. blade status --type create
2. blade create jvm throwCustomException --exception java.lang.Exception \
     --classname com.example.controller.DubboController --methodname hello
3. blade destroy <UID>

# Эксперимент 3

1. blade create cpu fullload
2. top
3. blade destroy <UID>
4. top

# Эксперимент 4

1. blade create cpu fullload --timeout 30
2. top

# Эксперимент 5

1. blade create network delay --interface lo --time 10 --timeout 20
2. ping lo

# Эксперимент 6

1. blade create network loss --percent 35 --interface lo --timeout 20
2. ping lo

# Эксперимент 7
     
1. blade create disk fill --size 1000 --timeout 10
2. df
