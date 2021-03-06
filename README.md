# GrailbirdUpdater

For the most of the people who know me online, I've been dying to get a copy of
my Twitter archive from Twitter for forever. I was finally given one and
decided to write a quick script to keep my own archive up-to-date.

Turns out the contents in the archive are partial/trimmed API responses from
the Twitter API, so it is actually possible to drop a whole API response in
there, do some sorting and update the archive.


## Installation

Install it yourself as:

    $ gem install grailbird_updater

Or add this line to your application's Gemfile:

    gem 'grailbird_updater'

And then execute:

    $ bundle

## Usage

```
grailbird_updater /path/to/twitter/archive
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## FAQ

* _I have a protected Twitter account, can I still use this updater with my Twitter archive?_

    Actually, yes! However, you will need to create your own "application" on
    Twitter and then use your own consumer key/secret pair to let the application
    use the oauth tokens for a user and then follow the authorization steps for
    a given protected user.

    Once you have auth'd the application for a protected user, you do not have to do
    it again, the consumer key/secret and oauth token/secret are stored in a YAML file
    at the root of your tweet archive.

    __IMPORTANT__ Do NOT commit or post your own consumer key/secret or your oauth
    token/secret anywhere.

    Note: you will only need to create a single application on Twitter even if you
    are using this to update multiple protected account. You can reuse the consumer
    key/secret and just authorize each account individually.

    Please see [this wiki article](https://github.com/DeMarko/grailbird_updater/wiki/Authorizing-grailbird_updater-to-work-with-Protected-Twitter-accounts) for step-by-step instructions.

* _How do I know if I have a Twitter archive?_

    Hopefully, you downloaded it from Twitter once the feature was made available
    to you and have their web application which can consume it.

    This gem only modifies what's in the `data` directory for a given archive,
    the rest of the files are provided by Twitter.

    To check if you can download a copy of your Twitter archive, go to your
    [Account Settings](https://twitter.com/settings/account) and scroll all
    the way to the bottom. If the feature is enabled for you, you should see
    a section labeled "Your Twitter Archive".

    The file structure looks somewhat like this (as of 19.12.12):


```
tweets
├── README.txt
├── css
│   └─ ... // provided by Twitter
├── data
│   ├── csv
│   │   ├── 2007_03.csv
│   │   ├── 2007_04.csv
│   │   ├── 2007_05.csv
│   │   ├─ ...
│   │   ├── 2012_10.csv
│   │   ├── 2012_11.csv
│   │   └── 2012_12.csv
│   └── js
│       ├── payload_details.js
│       ├── tweet_index.js
│       ├── tweets
│       │   ├── 2007_03.js
│       │   ├── 2007_04.js
│       │   ├── 2007_05.js
│       │   ├─ ... // you get the idea, I've been on Twitter a while
│       │   ├── 2012_10.js
│       │   ├── 2012_11.js
│       │   └── 2012_12.js
│       └── user_details.js
├── img
│   └─ ... // provided by Twitter
├── index.html
├── js
│   └─ ... // provided by Twitter
└── lib
    └─ ... // provided by Twitter
```

