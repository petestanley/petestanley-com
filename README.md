# petestanley.com frontend website

## Build
- run `hugo` to generate static site.
-  Upload content of public/ to web host.
    - `aws s3 sync ./public/ s3://petestanley.com --profile <YOUR_PROFILE>`
- Invalidate Cloudfront CDN:
    - List distributions
        - `aws cloudfront list-distributions --profile <YOUR_PROFILE> --output table`
    - Create invalidation:
        - `aws cloudfront create-invalidation --distribution-id <DISTRO_ID> --paths "/*" --profile <YOUR_PROFILE>`
    - Monitor invlidation status:
        - `aws cloudfront get-invalidation --distribution-id <DISTRO_ID> --id <INVALIDATION_ID> --profile <YOUR_PROFILE>`