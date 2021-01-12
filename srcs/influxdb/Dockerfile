# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: kdahl <kdahl@student.21-school.ru>         +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/11/26 18:58:42 by kdahl             #+#    #+#              #
#    Updated: 2020/11/26 18:58:44 by kdahl            ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine

RUN 	apk update && \
		apk add openrc

RUN		apk add influxdb

EXPOSE  8086

CMD     [ "influxd" ]