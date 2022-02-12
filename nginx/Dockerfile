ARG FRAPPE_BRANCH=develop
FROM node:14-buster
ARG FRAPPE_BRANCH=develop

ARG GITHUB_OWNER=default_github_owner # you could give a default value as well
ENV GITHUB_OWNER=$GITHUB_OWNER

COPY install_frappe.sh /install_frappe
COPY install_erpnext.sh /install_erpnext
COPY install_app.sh /install_app
COPY prepare_production.sh /prepare_production

# Install frappe
RUN /install_frappe ${FRAPPE_BRANCH} && \
  # Install erpnext
  /install_erpnext && \
  # Install required apps with following command
  # /install_app <app_name> <repo> <app_branch>
  /install_app metabase_integration https://github.com/${GITHUB_OWNER}/shrdc_frappe_metabase master && \
  /install_app bench_manager https://github.com/${GITHUB_OWNER}/shrdc_bench_manager develop && \
  /install_app erpnext_telegram_integration https://github.com/${GITHUB_OWNER}/shrdc_erpnext_telegram master && \
  /install_app barcode_shrdc https://github.com/leexy0/barcode_shrdc master && \
  /install_app frepple https://github.com/Drayang/ERPNext-Frepple master && \
  /install_app my_custom_maintenance https://github.com/msf4-0/ERPNext_my_custom__maintenance master && \
  /prepare_production

FROM frappe/erpnext-nginx:${FRAPPE_BRANCH}

COPY --from=0 /home/frappe/frappe-bench/sites/ /var/www/html/
COPY --from=0 /rsync /rsync

# Append list of installed to apps.txt
RUN echo -n "metabase_integration\nbench_manager" >> /var/www/html/apps.txt

VOLUME [ "/assets" ]

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]
