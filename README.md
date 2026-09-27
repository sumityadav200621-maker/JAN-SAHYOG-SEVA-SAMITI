# JAN-SAHYOG-SEVA-SAMITI
import os
import shutil

# Files
html_file = "index.html"
pdf_file = "documents.pdf"

# Assets folder create karo
os.makedirs("assets", exist_ok=True)

# PDF ko assets folder mein copy karo
shutil.copy2(pdf_file, "assets/documents.pdf")

# HTML read karo
with open(html_file, "r", encoding="utf-8") as file:
    html = file.read()

# Documents section mein PDF links ensure karo
old_link = "documents.pdf"
new_link = "assets/documents.pdf"

html = html.replace(
    'href="documents.pdf"',
    f'href="{new_link}"'
)

# Agar link pehle se assets/documents.pdf hai to kuch change nahi hoga
# Download filename bhi set kar do
html = html.replace(
    'download="documents.pdf"',
    'download="Jan-Sahayog-Samaj-Seva-Samiti-Documents.pdf"'
)

# Updated HTML save karo
with open(html_file, "w", encoding="utf-8") as file:
    file.write(html)

print("Website successfully updated!")
print("PDF location: assets/documents.pdf")
print("Documents section is ready.")
