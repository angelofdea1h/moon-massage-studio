# moon-massage-studio
from pathlib import Path
import zipfile

# Define file structure for the static site
project_root = Path("/mnt/data/moon-massage-studio")
project_root.mkdir(exist_ok=True)

# HTML placeholder file (could be from React build in real use)
index_html = project_root / "index.html"
index_html.write_text("""
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Moon Massage Studio</title>
  <style>
    body { font-family: sans-serif; background: #fdfcfa; color: #444; text-align: center; padding: 2rem; }
    h1 { color: #6b46c1; }
    a { background: #6b46c1; color: white; padding: 0.5rem 1rem; border-radius: 5px; text-decoration: none; }
  </style>
</head>
<body>
  <h1>MOON MASSAGE STUDIO</h1>
  <p>You need to find time for yourself.</p>
  <a href="https://wa.me/254755938707">Book a Session</a>
</body>
</html>
""")

# Create a ZIP file for optional manual upload
zip_path = Path("/mnt/data/moon-massage-studio.zip")
with zipfile.ZipFile(zip_path, "w") as zipf:
    for file in project_root.glob("**/*"):
        zipf.write(file, arcname=file.relative_to(project_root))

zip_path.name  # Return the ZIP file name for download if needed later
