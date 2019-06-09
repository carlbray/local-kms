
```bash
carl@octavo MINGW64 /d/docker/local-kms (master)
$ docker-compose up
```

```bash
root@octavo:/mnt/d/docker/local-kms# aws --endpoint-url http://localhost:8688 kms create-key
{
    "KeyMetadata": {
        "AWSAccountId": "111122223333",
        "KeyId": "590278ed-81e9-4be9-b101-0220d69e87f6",
        "Arn": "arn:aws:kms:ap-southeast-2:111122223333:key/590278ed-81e9-4be9-b101-0220d69e87f6",
        "CreationDate": 1559970541,
        "Enabled": true,
        "KeyUsage": "ENCRYPT_DECRYPT",
        "KeyState": "Enabled",
        "Origin": "AWS_KMS",
        "KeyManager": "CUSTOMER"
    }
}
```

```bash
root@octavo:/mnt/d/docker/local-kms# aws --endpoint-url http://localhost:8688 kms list-keys
{
    "Keys": [
        {
            "KeyId": "1fe45f93-ba81-4c32-a4dc-197ed61309d7",
            "KeyArn": "arn:aws:kms:ap-southeast-2:111122223333:key/1fe45f93-ba81-4c32-a4dc-197ed61309d7"
        },
        {
            "KeyId": "590278ed-81e9-4be9-b101-0220d69e87f6",
            "KeyArn": "arn:aws:kms:ap-southeast-2:111122223333:key/590278ed-81e9-4be9-b101-0220d69e87f6"
        },
        {
            "KeyId": "737eae78-1b4f-48c1-ad55-00324276f0db",
            "KeyArn": "arn:aws:kms:ap-southeast-2:111122223333:key/737eae78-1b4f-48c1-ad55-00324276f0db"
        },
        {
            "KeyId": "bc436485-5092-42b8-92a3-0aa8b93536dc",
            "KeyArn": "arn:aws:kms:ap-southeast-2:111122223333:key/bc436485-5092-42b8-92a3-0aa8b93536dc"
        }
    ]
}
```

```bash
root@octavo:/mnt/d/docker/local-kms# aws --endpoint-url http://localhost:8688 kms list-aliases
{
    "Aliases": [
        {
            "AliasName": "alias/testing",
            "AliasArn": "arn:aws:kms:ap-southeast-2:111122223333:alias/testing",
            "TargetKeyId": "bc436485-5092-42b8-92a3-0aa8b93536dc"
        }
    ]
}
```

```bash
root@octavo:~# aws --endpoint-url http://localhost:8688 kms generate-data-key --key-id alias/testing --key-spec AES_256
{
    "CiphertextBlob": "UGFybjphd3M6a21zOmFwLXNvdXRoZWFzdC0yOjExMTEyMjIyMzMzMzprZXkvYmM0MzY0ODUtNTA5Mi00MmI4LTkyYTMtMGFhOGI5MzUzNmRjAAAAAMiCFSnMFFBNeOsKUptk6QiQgpooL6zfw9aUtFooMRJq8hzaDblm485EDpLwH6U3gb4jnmaLp8Gi9JWjLA==",
    "Plaintext": "bB1X/2nX6M3Sf+/Qn85IRotKZuSHyonsv5HdSoU8ZSc=",
    "KeyId": "arn:aws:kms:ap-southeast-2:111122223333:key/bc436485-5092-42b8-92a3-0aa8b93536dc"
}
```

