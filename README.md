# Draft Academy
Learn to build a better tech blog.

## Dev Notes

- Build the site: `docker run --rm -it -v $PWD:/srv/jekyll jekyll/jekyll:latest jekyll build`
- Serve locally: `docker run --rm -it -v $PWD:/srv/jekyll --volume=$PWD/vendor/bundle:/usr/local/bundle -p 4000:4000 jekyll/jekyll:latest jekyll serve`

See the theme [Demo](https://artemsheludko.github.io/flexible-jekyll/)

### License

Copyright Portable CTO, LLC. All rights reserved.
