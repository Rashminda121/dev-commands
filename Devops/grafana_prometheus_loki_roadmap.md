# Learning Roadmap: Grafana, Prometheus, Loki, and Helm

---

## Phase 1: Grafana – The Visualization Layer
**Goal:** Understand how dashboards and visualizations work.

1. **Install Grafana locally**  
   - Use Docker:
     ```bash
     docker run -d -p 3000:3000 grafana/grafana
     ```
   - Access it via `http://localhost:3000` (default user: `admin/admin`).

2. **Create a dashboard**  
   - Explore panels: graph, table, gauge.  
   - Add sample data: you can use a CSV file or the built-in `TestData DB`.  

3. **Practice exercises**  
   - Create a graph showing CPU usage (dummy values).  
   - Add a table panel displaying top 5 items.  
   - Set up an alert if a value exceeds a threshold.  

---

## Phase 2: Prometheus – Metrics Collection
**Goal:** Learn how to collect and visualize metrics.

1. **Install Prometheus locally**  
   - Use Docker:
     ```bash
     docker run -d -p 9090:9090 prom/prometheus
     ```
   - Explore the Prometheus web UI at `http://localhost:9090`.

2. **Learn Prometheus concepts**  
   - **Targets:** What Prometheus scrapes (your apps).  
   - **Metrics:** Numeric values collected over time.  
   - **PromQL:** Query language for metrics.  

3. **Practical exercises**  
   - Run a sample app (like Nginx or Node.js).  
   - Configure Prometheus to scrape its metrics.  
   - Connect Prometheus as a data source in Grafana.  
   - Create dashboards for CPU, memory, or request metrics.  

---

## Phase 3: Loki – Logs Aggregation
**Goal:** Learn how to collect, store, and visualize logs.

1. **Install Loki and Promtail**  
   - Loki stores logs, Promtail collects them.  
   - Docker example for both:
     ```bash
     docker run -d -p 3100:3100 grafana/loki
     docker run -d -v /var/log:/var/log grafana/promtail
     ```

2. **Understand key concepts**  
   - **Labels:** Tags to index logs (like service name).  
   - **Streams:** Groups of logs with the same label set.  

3. **Practical exercises**  
   - Collect logs from a sample app (like Nginx).  
   - Query logs in Grafana (e.g., show errors only).  
   - Correlate logs with metrics: if CPU spikes, check logs at that time.  

---

## Phase 4: Helm – Deploy Everything on Kubernetes
**Goal:** Learn how to manage Grafana, Prometheus, and Loki at scale.

1. **Install Helm**  
   - On your machine:
     ```bash
     curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
     ```

2. **Deploy the stack using Helm charts**  
   - Prometheus + Grafana:
     ```bash
     helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
     helm install monitoring prometheus-community/kube-prometheus-stack
     ```
   - Loki:
     ```bash
     helm repo add grafana https://grafana.github.io/helm-charts
     helm install loki grafana/loki-stack
     ```

3. **Practical exercises**  
   - Access Grafana in Kubernetes.  
   - Visualize metrics and logs from your apps in the cluster.  
   - Practice upgrades and rollbacks with Helm.  

---

## Phase 5: Combine & Explore
- Create dashboards showing **both metrics (Prometheus) and logs (Loki)**.  
- Simulate issues: spike CPU or errors, and use Grafana to debug.  
- Explore alerting: send alerts via email or Slack when thresholds are crossed.  

---

**Pro Tip:**
- Focus on **one layer at a time**: first visualize, then metrics, then logs.  
- Use **Docker or Minikube** for practice before moving to real Kubernetes clusters.

