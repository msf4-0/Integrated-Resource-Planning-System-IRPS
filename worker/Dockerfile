ARG FRAPPE_BRANCH=develop
FROM frappe/erpnext-worker:${FRAPPE_BRANCH}

RUN install_app metabase_integration https://github.com/pipech/frappe-metabase master
