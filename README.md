# grpc-sample
grpcの学習用
# 参考
[作ってわかる！ はじめてのgRPC](https://zenn.dev/hsaki/books/golang-grpc-starting)
# 準備
```
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.28
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2
```
```
brew install grpcurl
```
# コードの生成
```
cd api

protoc --go_out=../pkg/grpc --go_opt=paths=source_relative \
	--go-grpc_out=../pkg/grpc --go-grpc_opt=paths=source_relative \
	sample.proto
```

# grpcサーバーの動作確認
## サーバーの起動
```
go run cmd/server/main.go
```
## サーバー内に実装されているサービス一覧の確認
```
grpcurl -plaintext localhost:8080 list
```
## サービスが持つメソッド一覧の確認
```
grpcurl -plaintext localhost:8080 list myapp.GreetingService
```
## メソッドの呼び出し
```
grpcurl -plaintext -d '{"name": "hsaki"}' localhost:8080 myapp.GreetingService.Hello
```
## クライアントの起動
```
go run cmd/client/main.go
```