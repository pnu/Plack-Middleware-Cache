# NAME

Plack::Middleware::Cache::CHI - Caching Reverse Proxy for Plack

# VERSION

version 0.101

# DESCRIPTION

Enable HTTP caching for Plack-based applications.

Mathing URI's (rules) are cached with the specified
expiry time / ttl value to the CHI cache.

Current implementation (on master branch) does not
support cache validation. See devel branch for work in
progress towards this.

    my $chi = CHI->new(
        driver => 'File',
        root_dir => 'common/cache',
    );

    enable 'Cache::CHI', chi => $chi, rules => [
        qr{^/api/}          => undef,
        qr{\.(jpg|png)$}    => { expires_in => '5 min' },
    ], scrub => [ 'Set-Cookie' ], cachequeries => 1;

# SEE ALSO

This module is largely based on Rack::Cache by Ryan Tomayko.
See http://rtomayko.github.com/rack-cache/ for more information.

This module was earlier called Plack::Middleware::Cache and available
only thru github because of name conflict with another similar CPAN module.

# AUTHOR

Panu Ervamaa &lt;pnu@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2011-2015 by Panu Ervamaa.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
