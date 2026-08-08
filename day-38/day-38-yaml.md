name: Bijaya Kumar Jena
role: Software Developer
experience_years: 2
learning: true




tools — a list of 5 DevOps tools you know or are learning

tools:
  - Docker
  - Kubernetes
  - Linux
  - Terraform
  - Ansible
  - Git & GitHub
  - Grafana
hobbies — [Shell Scripting, Docker Scripting, Linux Command]


server: 
  - name: Production-server
  - ip: 123.142.0.1 
  - port: 8000
database:
  - host: localhost
  - name: erp_db
  - credentials
      - user: admin
      - password: admin

  startup_script: |
  echo "Starting server..."
  python manage.py migrate
  python manage.py runserver 0.0.0.0:8000
  echo "Server started"

  startup_description: >
  This server starts the Django application
  after applying the required database migrations
  and then listens for incoming requests
  on port 8000.
# Block 1 - correct
name: devops
tools:
  - docker
  - kubernetes


