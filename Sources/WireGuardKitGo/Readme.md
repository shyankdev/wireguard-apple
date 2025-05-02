brew install wireguard-tools

GOOS=ios \
GOARCH=arm64 \
CC=$(xcrun --sdk iphoneos --find clang) \
CGO_CFLAGS="-fembed-bitcode -isysroot $(xcrun --sdk iphoneos --show-sdk-path) -arch arm64" \
CGO_LDFLAGS="-arch arm64 -isysroot $(xcrun --sdk iphoneos --show-sdk-path)" \
go build -tags ios -trimpath -v -buildmode=c-archive -o libwg-go.a
