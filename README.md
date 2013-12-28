# NAME

App::Uc::TwitterIrcGateway - Twitter IRC Gateway of me by me for me

# SYNOPSIS

## Start twitter irc gateway server

    $ perl utig.pl

## Login utig.pl server

- 1

    IRCクライアントで起動したサーバに適当な名前でログインする

- 2

    暫くするとサーバーから OAuth 認証用の URL を渡されるので、それを開いて認証する

- 3

    IRCクライアントで

        /pin <pin code>

    Welcome to utig.pl server!

好きにするといい！

# DESCRIPTION

utig.pl は userstream の監視プログラムに毛が生えた程度のTwitter IRCゲートウェイサーバです

# FEATURES

- UserStream を使用して閲覧するので発言が即座に流れてくるぞ！
- あんまり API を叩かない仕様だから他の Twitter 関連サービスと併用しても安心！
- コマンドと自前で作った TypableMap が快適な Twitter Life をサポートするぞ！

        コマンドは

            my @action_command_info = (qq|action commands:|
            ,  qq|/me mention (or me): fetch mentions|
            ,  qq|/me reply (or re) <tid> <text>: reply to a <tid> tweet|
            ,  qq|/me favorite (or f, fav) +<tid>: add <tid> tweets to favorites|
            ,  qq|/me unfavorite (or unf, unfav) +<tid>: remove <tid> tweets from favorites|
            ,  qq|/me retweet (or rt) +<tid>: retweet <tid> tweets|
            ,  qq|/me quotetweet (or qt, qw) <tid> <text>: quotetweet a <tid> tweet, like "<text> QT \@tid_user: tid_tweet"|
            ,  qq|/me delete (or del, oops) *<tid>: delete your <tid> tweets. if unset <tid>, delete your last tweet|
            ,  qq|/me list (or li) <screen_name>: list <screen_name>'s recent 20 tweets|
            ,  qq|/me information (or in, info) +<tid>: show <tid> tweets information. e.g. retweet_count, has conversation, created_at|
            ,  qq|/me conversation (or co) <tid>: show <tid> tweets conversation|
            ,  qq|/me ratelimit (or rate, limit): show remaining api hit counts|
            ,  qq|/me ngword (or ng) <text>: set/delete a NG word. if unset <text>, show all NG words|
            );

        こんなかんじだ！
- Lists 対応。ただしリストに入れていてもフォローしてない人の発言は流れてこないぞ！
しかも自分が作ったリストしか見れないぞ！
- MySQLにログたくさんとるぞ！
- Follow, unfollow, direct message, block, list, account の操作？そんなもんねぇ！
(いつか対応予定です)

# DEPENDENCIES

- [perl](http://search.cpan.org/perldoc?perl) >= 5.14
- [opts](http://search.cpan.org/perldoc?opts)
- [Net::Twitter::Lite](http://search.cpan.org/perldoc?Net::Twitter::Lite)
- [AnyEvent::Twitter](http://search.cpan.org/perldoc?AnyEvent::Twitter)
- [AnyEvent::Twitter::Stream](http://search.cpan.org/perldoc?AnyEvent::Twitter::Stream)
- [Clone](http://search.cpan.org/perldoc?Clone)
- [Config::Pit](http://search.cpan.org/perldoc?Config::Pit)
- [DateTime::Format::HTTP](http://search.cpan.org/perldoc?DateTime::Format::HTTP)
- [DateTime::Format::DateParse](http://search.cpan.org/perldoc?DateTime::Format::DateParse)
- [HTML::Entities](http://search.cpan.org/perldoc?HTML::Entities)

# BUGS AND LIMITATIONS

Please report any bugs or feature requests to
[https://github.com/UCormorant/p5-app-uc-twitterircgateway/issues](https://github.com/UCormorant/p5-app-uc-twitterircgateway/issues)

# AUTHOR

[https://twitter.com/c18t](https://twitter.com/c18t)

# LICENCE AND COPYRIGHT

Copyright (C) U=Cormorant.

This module is free software; you can redistribute it and/or
modify it under the same terms as Perl itself. See [perlartistic](http://search.cpan.org/perldoc?perlartistic).
