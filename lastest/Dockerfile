FROM base_odoo:14
MAINTAINER Hieutv26 <hieutv26@viettel.com.vn>

SHELL ["/bin/bash", "-xo", "pipefail", "-c"]

RUN useradd -ms /bin/bash odoo

COPY ./entrypoint.sh /entrypoint.sh

RUN chmod +x /entrypoint.sh

# source code odoo
COPY ./odoo/ /odoo/

ENV ODOO_BIN=/odoo/odoo-bin 
ENV ODOO_CONFIG=/odoo/config/odoo.conf 

# create path external
RUN mkdir -p /odoo/extra-addons
RUN mkdir -p /odoo/data_dir
RUN mkdir -p /odoo/config

RUN chown odoo /odoo

EXPOSE 8010 8069 8071 8072

VOLUME ["/odoo/extra-addons", "/odoo/data_dir", "/odoo/config"]

USER odoo

CMD ["./entrypoint.sh"]
#CMD ./entrypoint.sh

#CMD ["bash /entrypoint.sh", "container started"]