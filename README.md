# grpc-sample
grpcの学習用
# 参考
[作ってわかる！ はじめてのgRPC](https://zenn.dev/hsaki/books/golang-grpc-starting)
# 準備
```
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.28
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2
```
# コードの生成
```cd api```
```
protoc --go_out=../pkg/grpc --go_opt=paths=source_relative \
	--go-grpc_out=../pkg/grpc --go-grpc_opt=paths=source_relative \
	sample.proto
```