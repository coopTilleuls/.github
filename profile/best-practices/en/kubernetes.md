## Les-Tilleuls.coop’s Kubernetes Best Practices

- Always create a Helm chart (use https://github.com/api-platform/api-platform/tree/master/api/helm/api as a skeleton) and store it in the Git repository. Everything must be scripted, versioned and reproducible!
- Use Google Kubernetes Engine (unless asked explicitly to use another provider by the customer)
- Use CloudFlare with external-dns for DNS management and for SSL (do not use Let’s Encrypt). CloudFlare has many advantages over Let’s Encrypt: easier to setup, more secure by default, add DDOS protection, no rate limit... See also https://httpsiseasy.com/
- Always use managed persistence systems (Google Cloud SQL for DB or Google Cloud Storage for images, invoices, exports and imports files…). Managed services are safer (guaranteed SLA, automatic backup…) and usually more performant. Never use Kubernetes to host the RDMS or files!
- Always store static websites (including Single Page Applications and Progressive Web Apps) in static hosting systems (Firebase Hosting or GitHub Pages are recommended). It’s cheaper, safer and more performant. Do not use Kubernetes to host static websites. Be careful when using Google Storage because setting up SSL for Google Storage is hard. Prefer Firebase Hosting.
- Always work in a namespace, and never in the default namespace! It’s easier to destroy it to start from fresh. When creating branch deployments, the namespace must be the name of the branch.
- For branch deployment (not for prod deployments!)
- Don’t use the “latest” Docker tag for Kubernetes deployments. Always tag Docker container with the corresponding Git commit hash and tag (if applicable) to ease rollbacks and debug.
- Change “imagePullPolicy” to “Always” to force download fresh images.
- In production, use node with 3 servers minimum for High availability since update of Kubernetes
- When possible, use Alpine-based images to reduce the container’s size
- Only use official Docker images (maintained by the Docker team, the upstream editor or known and recognized contributors). Create custom Dockerfiles if there is no official image available.
