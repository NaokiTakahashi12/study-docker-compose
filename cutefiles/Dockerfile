FROM node
RUN npm install -g cute-files2@1.0.3
RUN sed -i 's/http:\/\//\/\//g' \
        /usr/local/lib/node_modules/cute-files2/frontend/index.html
WORKDIR /cutefiles
EXPOSE 3000
CMD ["/usr/local/bin/cute-files"]
