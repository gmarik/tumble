# Tumble #
A Ruby wrapper for the v2 of Tumblr's API, supporting all endpoints.

## <a name="installation"></a>Installation
    gem install tumble

## <a name="configuration"></a>Configuration

The gem is designed to work with Tumblr's OAuth provider for authentication. If you're using omniauth,
there's a fine adapter available [here][https://github.com/aub/omniauth-tumblr2]. You'll also need to
register your app [here][http://www.tumblr.com/oauth/apps] in order to get a consumer key and secret.
Once you have those values, you can configure Tumble in an initializer like so:

    require 'tumble'

    Tumble.configure do |tumble|
      tumble.consumer_key = config['tumblr']['key']
      tumble.consumer_secret = config['tumblr']['secret']
    end

Connections can then be made by creating a client, passing the OAuth token and secret you get back from
omniauth:

    client = Tumble::Client.new(access_token, access_secret)

User-related endpoints can be accessed through the client directly, as documented [here][http://rdoc.info/github/aub/tumble/Tumble/Client].
For example:

    client.user_info

All methods will return a Hashie::Mash of the results. For data about blogs and posts, use the blog() method on
the client, passing the name of the blog. The methods for blogs are documented [here][http://rdoc.info/github/aub/tumble/Tumble/Blog].
For example, getting posts for a specific blog can be done like this:

    client.blog('www.riotprojects.com').posts

Most of the calls allow for options to be passed, as a hash. Options are documented in the links above and are consistent
with the naming and functionality described in the [Tumblr docs][https://github.com/aub/omniauth-tumblr2].

## <a name="documentation"></a>Documentation
[http://rdoc.info/github/aub/tumble][documentation]

[documentation]: http://rdoc.info/github/aub/tumble

## <a name="copyright"></a>Copyright
Copyright (c) 2012 Aubrey Holland
See [LICENSE][] for details.

[license]: https://github.com/aub/tumble/blob/master/LICENSE.md

