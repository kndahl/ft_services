# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: kdahl <kdahl@student.21-school.ru>         +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/11/26 18:44:55 by kdahl             #+#    #+#              #
#    Updated: 2020/11/26 18:45:20 by kdahl            ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine

RUN 	apk update && apk add openrc 
RUN		apk add nginx && apk add supervisor
RUN		apk add openssl && apk add openssh
RUN		adduser -D 'kdahl'; echo "kdahl:1" | chpasswd;
RUN 	openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
		-subj '/C=RU/ST=Moscow/L=Moscow/O=42/OU=21/CN=kdahl' \
		-keyout /etc/ssl/localhost.key \
		-out /etc/ssl/localhost.crt
RUN		mkdir www

COPY	./srcs/index.html /www/
COPY 	./srcs/nginx.conf /etc/nginx/conf.d/default.conf
COPY 	./srcs/supervisord.conf /etc/supervisord.conf
COPY 	./srcs/start.sh start.sh

RUN 	chmod +x start.sh

EXPOSE	80 443 22

CMD		[ "sh", "start.sh" ]