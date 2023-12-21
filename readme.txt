
--------------------------------------------------------------------------------

			# RABBITMQ-STUDY #

---------------------------------------------------------------------------------

https://www.rabbitmq.com/

	+---+   +---+
	|   |   |   |
	|   |   |   |
	|   |   |   |
	|   +---+   +-------+
	|                   |
	| RabbitMQ  +---+   |
	|           |   |   |
	|           +---+   |
	|                   |
	+-------------------+
-------------------------------------------	

-Reference
# Message Queue
https://weicomes.tistory.com/18
https://12bme.tistory.com/176
https://heowc.tistory.com/35

# Message Queue 사용 이유
https://www.icelancer.com/2016/12/message-queue.html
	
-------------------------------------------	

# RabbitMQ 설명
https://skibis.tistory.com/310
https://nesoy.github.io/articles/2019-02/RabbitMQ 	
https://jonnung.dev/rabbitmq/2019/02/06/about-amqp-implementtation-of-rabbitmq/		
	
-------------------------------------------	

-Get Started
https://www.rabbitmq.com/#getstarted

	-Downloading and Installing RabbitMQ

	1.Erlang 설치 - otp_win64_21.3.exe
	https://www.erlang.org/downloads
	Erlang must be installed using an administrative account
	install path : C:\dev\erl10.3
	env set : ERLANG_HOME = C:\dev\erl10.3\erts-10.3
	env set : ERLANG_SERVICE_MANAGER_PATH = C:\dev\erl10.3\erts-10.3
		
	2.RabbitMQ 설치 - rabbitmq-server-3.8.5.exe
	https://www.rabbitmq.com/download.html
	https://www.rabbitmq.com/install-windows.html
	install path : C:\dev\RabbitMQ Server

	-RabbitMQ Tutorials
	https://www.rabbitmq.com/getstarted.html
	source : https://github.com/rabbitmq/rabbitmq-tutorials
 	
-------------------------------------------	

-RabbitMQ 실행
 RabbitMQ Server > RabbitMQ service - start
	
-RabbitMQ 종료
 RabbitMQ Server > RabbitMQ service - stop

-RabbitMQ 관리콘솔 활성화 - 
https://www.rabbitmq.com/management.html
https://rumblefish.tistory.com/75

-활성화 명령 실행 후 RabbitMQ 재 시작 
C:\dev\RabbitMQ Server\rabbitmq_server-3.8.5\sbin\rabbitmq-plugins.bat enable rabbitmq_management

url   : http://lcoalhost:15672/
id/pw : guest/guest (default 계정)

-------------------------------------------	

RabbitMQ Tutorials Source (java)
https://github.com/rabbitmq/rabbitmq-tutorials/tree/master/java

import library
https://repo1.maven.org/maven2/com/rabbitmq/amqp-client/5.6.0/amqp-client-5.6.0.jar
https://repo1.maven.org/maven2/org/slf4j/slf4j-api/1.7.25/slf4j-api-1.7.25.jar
https://repo1.maven.org/maven2/org/slf4j/slf4j-simple/1.7.25/slf4j-simple-1.7.25.jar

set CP=.;amqp-client-5.6.0.jar;slf4j-api-1.7.25.jar;slf4j-simple-1.7.25.jar

-전체 요약
https://bigboss.io/2017/04/the-channel-interface-of-the-rabbitmq-java-client-library/
https://kimseunghyun76.tistory.com/422?category=687132


1. Tutorial one: "Hello World!":
	https://www.rabbitmq.com/tutorials/tutorial-one-java.html
	https://kimseunghyun76.tistory.com/423?category=687132
	
	# terminal tab 1
	java -cp %CP%  Recv

	# terminal tab 2
	java -cp %CP%  Send
   
2. Tutorial two: Work Queues:
	https://www.rabbitmq.com/tutorials/tutorial-two-java.html
	https://kimseunghyun76.tistory.com/424?category=687132
	
	# terminal tab 1
	java -cp %CP% NewTask

	# terminal tab 2
	java -cp %CP% Worker

3. Tutorial three: Publish/Subscribe
	https://www.rabbitmq.com/tutorials/tutorial-three-java.html
	https://kimseunghyun76.tistory.com/425?category=687132

	# terminal tab 1
	java -cp %CP% ReceiveLogs

	# terminal tab 2
	java -cp %CP% EmitLog
	
4. Tutorial four: Routing
	https://www.rabbitmq.com/tutorials/tutorial-four-java.html	
	https://kimseunghyun76.tistory.com/426?category=687132

	# terminal tab 1
	java -cp %CP% ReceiveLogsDirect warning error

	# terminal tab 2
	java -cp %CP% ReceiveLogsDirect info warning error

	# terminal tab 3
	java -cp %CP% EmitLogDirect error "Run. Run. Or it will explode."
	java -cp %CP% EmitLogDirect info "Run. Run. Or it will explode."
	java -cp %CP% EmitLogDirect warning "Run. Run. Or it will explode."

5. Tutorial five: Topics
	https://www.rabbitmq.com/tutorials/tutorial-five-java.html	
	https://kimseunghyun76.tistory.com/427?category=687132

	# To receive all the logs:
	java -cp %CP% ReceiveLogsTopic "#"

	# To receive all logs from the facility "kern":
	java -cp %CP% ReceiveLogsTopic "kern.*"

	# Or if you want to hear only about "critical" logs:
	java -cp %CP% ReceiveLogsTopic "*.critical"

	# You can create multiple bindings:
	java -cp %CP% ReceiveLogsTopic "kern.*" "*.critical"

	# And to emit a log with a routing key "kern.critical" type:
	java -cp %CP% EmitLogTopic "kern.critical" "A critical kernel error"	

6. Tutorial six: RPC
	https://www.rabbitmq.com/tutorials/tutorial-six-java.html
	https://kimseunghyun76.tistory.com/428?category=687132

	# Our RPC service is now ready. We can start the server:
	java -cp %CP% RPCServer

	# To request a fibonacci number run the client:
	java -cp %CP% RPCClient
	
7. Tutorial seven: Publisher Confirms
	https://www.rabbitmq.com/tutorials/tutorial-seven-java.html

	java -cp %CP% PublisherConfirms	
	
8. Tutorial eight: Headers Exchange
-------------------------------------------	


