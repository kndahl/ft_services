# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: kdahl <kdahl@student.21-school.ru>         +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/11/26 20:04:17 by kdahl             #+#    #+#              #
#    Updated: 2020/11/26 20:04:20 by kdahl            ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine

RUN 	apk update && \
		apk add openrc 

RUN		apk add mysql mysql-client && \
		mkdir "/run/mysqld" && \
		chown -R mysql /run/mysqld

COPY	./srcs/createdb.sql ./srcs/base.sql ./srcs/start.sh ./

COPY	./srcs/my.cnf /etc/my.cnf

EXPOSE	3306

CMD		[ "sh", "start.sh" ]