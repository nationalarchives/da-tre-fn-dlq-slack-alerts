FROM public.ecr.aws/lambda/python:3.14
ARG PIP_INDEX_URL

# Copy function code
COPY tre_dlq_slack_alerts.py ${LAMBDA_TASK_ROOT}

# Install the function's dependencies using file requirements.txt
COPY requirements.txt ./requirements.txt
RUN dnf update -y --security
RUN dnf clean all --enablerepo=\*
RUN pip install --no-cache-dir --requirement requirements.txt --target "${LAMBDA_TASK_ROOT}"

# Set the CMD to your handler (could also be done as a parameter override outside of the Dockerfile)
CMD [ "tre_dlq_slack_alerts.lambda_handler" ]
