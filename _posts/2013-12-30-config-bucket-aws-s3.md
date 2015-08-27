---
layout: post
title: Configurar um Bucket S3 na AWS S3
tags:
- beginner
- aws
- s3
- iam
---
Sempre que preciso fazer upload de documentos, uso o serviço da Amazon chamado:
Simple Storage Service, mais conhecido como [Amazon S3](www.amazon.com/s3).
Neste texto pretendo ter um passo-a-passo para me lembrar como fazer isso.

Para acesso aos buckets é necessário criar um usuário no serviço:
AWS Identity and Access Management [IAM](https://aws.amazon.com/iam/).
Que é o serviço de identidade da Amazon para acesso aos serviços.

Passo-a-passo:

  1. Cria o bucket no Amazon S3. Eu gosto de nomear o bucket assim: nome_do_projeto-ambiente. Por exemplo: beyondclick_blog-production
  1. Cria o usuário no IAM. Eu uso o mesmo nome do bucket: https://console.aws.amazon.com/iam/home?#users
   * Gravar as informações de: Access Key ID e Secret Access Key.
  1. Configura permissão para o usuário criado:

{% highlight bash %}
# Permissions > Attach User Policy > Custom Policy > Select >
# Policy Name: bucket_<project>-<development | production>
# Policy Document:
{
    "Statement": [
        {
            "Sid": "AllowPublicRead",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:s3:::<project>-<development | production>/*"
            ]
        }
    ]
}
{% endhighlight %}

```xml
# Permissions > Attach User Policy > Custom Policy > Select >
# Policy Name: bucket_<project>-<development | production>
# Policy Document:
{
    "Statement": [
        {
            "Sid": "AllowPublicRead",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:PutObjectAcl"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:s3:::<project>-<development | production>/*"
            ]
        }
    ]
}
```

  1. Exportar a variável de ambiente no Heroku:

```bash
heroku config:set AMAZON-S3_BUCKET=project-production
heroku config:set AMAZON-IAM_ACCESS-KEY-ID=<Informado pela Amazon IAM>
heroku config:set AMAZON-IAM_SECRET-ACCESS-KEY=<Informado pela Amazon IAM>
```

Pronto. Com isso já posso acessar usando o Paperclip :)

Como assim? Não sabe fazer [upload de arquivos para o S3 usando Ruby]({% post_url 2014-01-18-s3-upload-the-simplest-possible-in-ruby %})?

Dúvidas, críticas ou sugestões, a parte de comentários é pra isso, mesmo. ;)
