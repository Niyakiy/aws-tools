# AWS Tools
Various AWS tools for daily usage.

## aws_glacier_upload.py

Helper script to upload data to [AWS Glacier](https://docs.aws.amazon.com/amazonglacier/latest/dev/introduction.html). 

Typical usage:
```bash
aws_glacier_upload.py \
    --vault-name "My-BACKUP" \
    --file-name my-backup-file.tar.gz \
    --region eu-west-1 \
    --arc-desc "My 1st Glacier backup" \
    --part-size 512 \
    --num-threads 1
```
where<br>
* `--vault-name` Your Glacier's Vault name
* `--file-name` Local file to upload to Glacier (better to use one huge file like tar archive instead of hundreds of small files)
* `--region` Indicate where to connect to Glacier
* `--arc-desc` Put some description here
* `--part-size` Chunk size to upload at once (Mb). Max is 4000Mb.
* `--num-threads` How many chunks will be uploaded in parallel. Make sure to have `part-size * num-threads` Mb available memory to proceed.

