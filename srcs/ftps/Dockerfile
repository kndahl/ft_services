# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: kdahl <kdahl@student.21-school.ru>         +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/11/26 18:56:52 by kdahl             #+#    #+#              #
#    Updated: 2020/11/26 19:06:40 by kdahl            ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine

RUN 	apk update && \
        apk add openrc 
RUN	apk add vsftpd && \
        apk add openssl

RUN     openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
        -subj '/C=RU/ST=Moscow/L=Moscow/O=42/OU=21/CN=kdahl' \
        -keyout /etc/ssl/private/vsftpd.key \
        -out /etc/ssl/certs/vsftpd.crt
RUN     adduser -D -h /var/ftp kdahl; echo "kdahl:1" | chpasswd
RUN     mkdir -p /var/ftp

COPY    /srcs/vsftpd.conf /etc/vsftpd/vsftpd.conf
COPY    /srcs/start.sh .

RUN     chmod +x start.sh

EXPOSE  20 21 44000
CMD     [ "sh", "start.sh" ]