# aws-signer-notation-ecr
Action `aws-ecr-signer` to generate or inspect image sign


####  Prerequisites
AWS Signer Profile with required ECR permissions need to be configured

####  Context
This action allows the workflow to build VOL API artifact

####  Inputs
- aws_signer_profile_arn (optional): AWS Signer Profile ARN if `image_sign_create` is set to `true`
- ecr_tagged_image (required): AWS ECR Image: {ACCOUNT_ID}.dkr.ecr.{REGION}.amazonaws.com/{REPO_NAME}:{IMAGE_TAG}
- image_sign_create (optional): Sign image if `true`
- image_sign_inspect (optional): Inspect sign if `true`

####  Outputs
N/A

####  Usage
```yaml
- name: Inspect image sign
  uses: anhussain90/aws-ecr-signer/.github/actions/aws-ecr-signer@main
  with:
    ecr_tagged_image: ${ACCOUNT_ID}.dkr.ecr.${REGION}.amazonaws.com/${REPO_NAME}:${IMAGE_TAG}
    image_sign_inspect: 'true'

- name: Create image sign
  uses: anhussain90/aws-ecr-signer/.github/actions/aws-ecr-signer@main
  with:
    aws_signer_profile_arn: ${ aws_signer_profile }
    ecr_tagged_image: ${ACCOUNT_ID}.dkr.ecr.${REGION}.amazonaws.com/${REPO_NAME}:${IMAGE_TAG}
    image_sign_inspect: 'true'
```