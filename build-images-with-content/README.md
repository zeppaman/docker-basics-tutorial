# Build an image with embedded contents
This put  content into an image during build. It is useful to provide your own image with inside your ready application.

This is very simple, just use COPY command to add contents

COPY http /var/tmp/

Using the right combination of "RUN" and "COPY" you will be able to realize all your forbidden dreams, or quite.