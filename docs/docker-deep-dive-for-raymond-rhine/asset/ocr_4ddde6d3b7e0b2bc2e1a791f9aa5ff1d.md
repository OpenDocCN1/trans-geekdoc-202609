Some instructions create new layers, whereas others add metadata.

Examples of instructions that create new layers are **FROM**, **RUN**, **COPY** and **WORKDIR**. Examples that create metadata include **EXPOSE**, **ENV**, **CMD**, and **ENTRYPOINT**. The premise is this:

+   - Instructions that add *content*, such as files and programs, create new layers

+   - Instructions that don't add content don't add layers and only create metadata

You can run a **docker history** command against any image to see the instructions that created it.

| docker history ddd-book:ch8.node |
| IMAGE | CREATED BY | SIZE |
| :--- | :--- | :--- |
| 24dd...a06b | CMD ["/bin/sh" "-c" "node app.js"] | 0B |
| <missing> | EXPOSE map[8080/tcp:{}] | 0B |
| <missing> | COPY # buildkit | 8kB |
| <missing> | USER node | 0B |
| <missing> | RUN /bin/sh -c npm ci --omit=dev # buildkit | 12.8M |
| <missing> | WORKDIR /usr/src/app | 16.4K |
| <missing> | ENV NODE_ENV=production | 0B |
| <missing> | /bin/sh -c #(nop) CMD ["node"] | 0B |
| <Snip> | /bin/sh -c #(nop) ADD file:ff311282967e8... | 8.35M |