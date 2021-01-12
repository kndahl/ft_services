# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: kdahl <kdahl@student.21-school.ru>         +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/11/26 18:58:34 by kdahl             #+#    #+#              #
#    Updated: 2020/11/26 18:58:36 by kdahl            ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine

RUN 	apk update && \
        apk add openrc 
RUN     apk add grafana --repository=http://dl-3.alpinelinux.org/alpine/edge/testing/

COPY    srcs/start.sh /
COPY    srcs/grafana.ini /usr/share/grafana/conf/custom.ini
COPY    srcs/datasources.yaml /usr/share/grafana/conf/provisioning/datasources/influxdb.yaml
COPY    srcs/dashboards.yaml /usr/share/grafana/conf/provisioning/dashboards/influxdb.yaml

RUN     mkdir -p /var/lib/grafana_dashboards/

COPY    srcs/dashboards/. /var/lib/grafana_dashboards/

EXPOSE  3000

CMD     [ "sh", "start.sh" ]