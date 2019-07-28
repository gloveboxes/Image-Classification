```bash
docker run -p 80:80 --name classifier --rm cv:latest
```

```bash
for i in {1..10000}; do time curl -X POST http://127.0.0.1/image -F imageData=@orange.jpg; echo $i; done
```