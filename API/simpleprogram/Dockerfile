FROM eclipse-temurin:17-jdk-alpine
WORKDIR /simpleprogram
COPY Main.java .
RUN javac Main.java

FROM eclipse-temurin:17-jre-alpine
WORKDIR /simpleprogram
COPY --from=0 /simpleprogram/Main.class .
ENTRYPOINT ["java", "Main"]