# Requests

[![](https://img.shields.io/github/license/cvelab/requests?style=flat-square)](https://github.com/cvelab/requests/blob/main/LICENSE)
[![](https://img.shields.io/badge/made%20by-cvelab-blue?style=flat-square)](https://github.com/cvelab)
[![](https://img.shields.io/github/go-mod/go-version/cvelab/requests?style=flat-square)](https://go.dev/)
[![](https://img.shields.io/github/v/tag/cvelab/requests?style=flat-square)](https://github.com/cvelab/requests)

[![Go Report Card](https://goreportcard.com/badge/github.com/cvelab/requests)](https://goreportcard.com/report/github.com/cvelab/requests)
[![CodeFactor](https://www.codefactor.io/repository/github/cvelab/requests/badge)](https://www.codefactor.io/repository/github/cvelab/requests)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fcvelab%2Frequests.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fcvelab%2Frequests?ref=badge_shield)

<h1 align="center"><img src="https://raw.githubusercontent.com/cvelab/requests/main/docs/static/logo.png" alt="Logo"/></h1>

## Install

```shell
go get github.com/cvelab/requests
```

## Demo

```golang
import (
    "fmt"
    "github.com/cvelab/requests"
    "github.com/cvelab/requests/ext"
    "github.com/cvelab/requests/types"
)

func main() {
    // Requests Bearer Token
    auth := types.BasicAuth{Username: "o94KGT3MlbT...", Password: "fNbL2ukEGyvuGSM7bAuoq..."}
    data := types.Dict{
        "grant_type": "client_credentials",
    }
    resp := requests.Post("https://api.twitter.com/oauth2/token", ext.Auth(auth), ext.Data(data))
    
    // Requests with Twitter API 2.0
    if resp != nil && resp.Ok {
        fmt.Println(resp.Json())
        token := types.BearerAuth{Token: resp.Json().Get("access_token").Str}
        resp2 := requests.Get("https://api.twitter.com/2/users/by/username/Sariel_D", ext.Auth(token))
        fmt.Println(resp2.Json())
    }
}
```

## Document

- [说明文档](https://requests.cvelab.com)

## Licenses

[MIT License](https://github.com/cvelab/requests/blob/main/LICENSE)

[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fcvelab%2Frequests.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fcvelab%2Frequests?ref=badge_large)
