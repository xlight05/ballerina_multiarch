# Auto Generated Dockerfile
FROM ghcr.io/graalvm/native-image:ol8-java11-22.3.3 as build

WORKDIR /app/build

COPY bal_multiarch.jar .

RUN native-image -jar bal_multiarch.jar -H:Name=bal_multiarch --no-fallback -H:+StaticExecutableWithDynamicLibC

FROM gcr.io/distroless/base

WORKDIR /home/ballerina

EXPOSE  8080
COPY --from=build /app/build/bal_multiarch .

CMD ["./bal_multiarch"]

