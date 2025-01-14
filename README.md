# Google Photos API client (Go library)
[![Build Status](https://img.shields.io/travis/com/gphotosuploader/google-photos-api-client-go.svg?style=flat-square)](https://travis-ci.com/gphotosuploader/google-photos-api-client-go)
[![Go Report Card](https://goreportcard.com/badge/github.com/gphotosuploader/google-photos-api-client-go)](https://goreportcard.com/report/github.com/gphotosuploader/google-photos-api-client-go)

This is a [Google Photos API client]() based on the official Google Photos API client library, that [was removed](https://code-review.googlesource.com/c/google-api-go-client/+/39951) from [Google API client library for Go](https://godoc.org/google.golang.org/api) and it was mirrored [here](https://github.com/gphotosuploader/googlemirror). 

Contains two packages:

- [![Go Documentation](https://img.shields.io/badge/go-documentation-blue.svg?style=flat-square)](https://godoc.org/github.com/gphotosuploader/google-photos-api-client-go/lib-gphotos) [lib-gphotos](https://github.com/gphotosuploader/google-photos-api-client-go/tree/master/lib-gphotos): simply wraps the official library to offer the same functionality plus uploads.
- [![Go Documentation](https://img.shields.io/badge/go-documentation-blue.svg?style=flat-square)](https://godoc.org/github.com/gphotosuploader/google-photos-api-client-go/noserver-gphotos) [noserver-gphotosclient](https://github.com/gphotosuploader/google-photos-api-client-go/noserver-gphotosclient) for being used in a CLI tool.    

## Quick start

Download using `go get github.com/gphotosuploader/google-photos-api-client-go`

Then use this way:

```
import "github.com/gphotosuploader/google-photos-api-client-go/noserver-gphotos"

func main() {
	// ask the user to authenticate on google in the browser
	photosClient, err := gphotosclient.NewClient(
		gphotosclient.AuthenticateUser(
			gphotoslib.NewOAuthConfig(gphotoslib.APIAppCredentials{
				ClientID:     "your-google-client-id",
				ClientSecret: "very_secret",
			}),
		),
	)
	if err != nil {
		log.Fatal(err)
	}

	_, err = photosClient.UploadFile("/path/to/file")
	if err != nil {
		log.Fatal(err)
	}
}
```
