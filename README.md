# Chef::Handler::SlackReporting

The chef-handler-slack gem is a Chef report mechanism that sends
failures to a Slack channel.

## Deprecated

Recent Slack changes no longer accept the team specific webhook urls, so this gem does not work anymore.

It is recommended to use [rackspace-cookbooks/chef-slack_handler](https://github.com/rackspace-cookbooks/chef-slack_handler) instead of this gem.

## Usage

Create a new recipe, with the following contents, and add it to the runlist of your base role in Chef:

```ruby
chef_gem "chef-handler-slack" do
  action :upgrade
end

require 'chef/handler/slack'

chef_handler "Chef::Handler::SlackReporting" do
  source "chef/handler/slack"
  arguments [
    # The name of your team registered with Slack
    :team => "tinyspeck",

    # Your incoming webhook token
    :token => "someawesometoken",

    # An existing channel
    :channel => "#chef",

    # Watever.
    :icon_emoj => ":chef:",
  ]
  action :nothing
end.run_action(:enable)
```

## Contributing

1. Fork it ( https://github.com/[my-github-username]/chef-handler-slack/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
