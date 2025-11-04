import os
import zipfile

# Create directory structure for ads-rich project
base_dir = "/mnt/data/ads-rich"
backend_dir = os.path.join(base_dir, "backend")
frontend_dir = os.path.join(base_dir, "frontend")
os.makedirs(backend_dir, exist_ok=True)
os.makedirs(frontend_dir, exist_ok=True)

# Write placeholder README
readme_content = """# ads Rich Courier & Logistics

This archive contains the full stack web app (frontend + backend) for the Rich Courier & Logistics tracking system.
Refer to ChatGPT instructions for deployment with Docker or manual setup.

Contact: richdelivery@aol.com
"""
with open(os.path.join(base_dir, "README.txt"), "w") as f:
    f.write(readme_content)

# Create zip archive
zip_path = "/mnt/data/ads-rich-tracking-site.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as zipf:
    for root, dirs, files in os.walk(base_dir):
        for file in files:
            filepath = os.path.join(root, file)
            arcname = os.path.relpath(filepath, base_dir)
            zipf.write(filepath, arcname)

zip_path
