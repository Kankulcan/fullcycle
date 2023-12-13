#Inicia o container com a imagem do golang.
FROM golang:1.19 as builder

WORKDIR /app 

COPY . .

#Realiza o build do projeto com as seguintes características.
#CGO_ENABLED=0 para não termos dependências externas no projeto.
#GOOS=linux para definirmos o sistema operacional.
#Output com outro nome.
RUN CGO_ENABLED=0 GOOS=linux go build -o fullcycle3.0 .

#Utilizamos a image scratch.
#Copiamos apenas o executável da imagem acima.
#Definimos o comando que será executado.
FROM scratch

WORKDIR /fullcycle

COPY --from=builder /app/fullcycle3.0 .

CMD [ "/fullcycle/fullcycle3.0" ]