# Get Started
> docker compose up -d

> go get github.com/IBM/sarama github.com/gin-gonic/gin

# Start Producer
> go run cmd/producer/producer.go

# Start Consumer
> go run cmd/consumer/consumer.go


# Sending notifications
With both producer and consumer running, you can simulate sending notifications. Open up a third terminal and use the below curl commands to send notifications:

## User 1 (Emma) receives a notification from User 2 (Bruno):
```bash
curl -X POST http://localhost:8080/send \
-d "fromID=2&toID=1&message=Bruno started following you."
```
## User 2 (Bruno) receives a notification from User 1 (Emma):
```bash
curl -X POST http://localhost:8080/send \
-d "fromID=1&toID=2&message=Emma mentioned you in a comment: 'Great seeing you yesterday, @Bruno!'"
```
## User 1 (Emma) receives a notification from User 4 (Lena):
```bash
curl -X POST http://localhost:8080/send \
-d "fromID=4&toID=1&message=Lena liked your post: 'My weekend getaway!'"
```

# Retrieving notifications
Finally, you can fetch the notifications of a specific user. You can use the below curl commands to fetch notifications:

## Retrieving notifications for User 1 (Emma):

```bash
curl http://localhost:8081/notifications/1
```
