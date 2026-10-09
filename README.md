# kaylisgarden.com 🌸🌱

A cute, pink garden-themed personal website for **Kayli Cameron**.

This project mirrors the lightweight, containerized architecture of [`lionslineuplab.com`](../lionslineuplab.com):
- **Frontend**: Responsive, modern placeholder website with soft rose & blossom styling, gentle ambient petals, and interactive elements.
- **Server**: Nginx Alpine container serving static assets on port `8080`.
- **CI/CD & Hosting**: Google Cloud Build pipeline deploying directly to Google Cloud Run (`kaylisgarden-www`).

---

## Directory Layout

```text
kaylisgarden.com/
├── .gitignore             # Standard git exclusions
├── README.md              # Project documentation & deployment guide
├── contact_info.yaml      # Registration contact metadata for kaylisgarden.com
└── www/
    ├── .dockerignore      # Files excluded from container build
    ├── Dockerfile         # Nginx Alpine container definition
    ├── cloudbuild.yaml    # Google Cloud Build pipeline configuration
    ├── index.html         # Cute pink garden placeholder homepage
    └── nginx.conf         # Nginx web server routing (port 8080)
```

---

## Preview Locally

### View Directly in Browser:
```bash
open www/index.html
```

### Run with Docker:
```bash
cd www
docker build -t kaylisgarden-www .
docker run -p 8080:8080 kaylisgarden-www
```
Then visit `http://localhost:8080`.

---

## Registering & Deploying `kaylisgarden.com`

### 1. Register the Domain Name
You can register `kaylisgarden.com` via:
- **Google Cloud Domains** (in the Google Cloud Console)
- Or any ICANN registrar (like [Namecheap](https://namecheap.com), [Porkbun](https://porkbun.com), or [Squarespace](https://domains.squarespace.com)).
- Use the contact information template in [`contact_info.yaml`](contact_info.yaml) for your registration details.

### 2. Deploy to Google Cloud Run
Deploy using the included Cloud Build configuration:
```bash
gcloud builds submit --config=www/cloudbuild.yaml .
```

### 3. Connect the Domain to Cloud Run
In the Google Cloud Console:
1. Navigate to **Cloud Run** > **Custom Domains** (or **Manage Custom Domains**).
2. Click **Add Mapping** and choose service `kaylisgarden-www`.
3. Enter `kaylisgarden.com` (and `www.kaylisgarden.com`).
4. Add the provided DNS `A` / `CNAME` records to your domain's DNS settings. Cloud Run automatically generates and manages your free SSL certificate!
