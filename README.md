## Chef LWRP for installing zsh/oh-my-zsh

====================

This is a nice clean LWRP for installing zsh and [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh) 
through [chef.](http://opscode.com/chef) 


Setup
-----
Just add oh_my_zsh as one of your dependencies in your metadata.rb.

Usage
-----
Simply pass a username to this LWRP and zsh/oh-my-zsh will be installed, the .zshrc template will be 
rendered, and zsh will be set as the default shell for that user.

```ruby
oh_my_zsh 'username'
```

Additionally you can specify the theme, plugins, and aliases you want using the appropriate resources.

```ruby
oh_my_zsh 'username' do
  theme 'theme'
  plugins ['git', 'rbenv', 'vagrant']
  aliases :be => 'bundle exec', :rs => 'bundle exec rails server'
end
```

If you wish to customize your .zshrc file outside of Chef you can modify the manage_zshrc resource.
if set to false the .zshrc file will not be rendered. This may be useful if you 
are deploying your dot-files through some other method.

```ruby
oh_my_zsh 'username' do
  manage_zshrc false
end
```

Yay! Less typing in the future!!!
