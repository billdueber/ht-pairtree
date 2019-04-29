# HathiTrust::Pairtree

Get a [Pairtree](https://github.com/mlibrary/pairtree) or [Pathname](http://ruby-doc.org/stdlib-2.6/libdoc/pathname/rdoc/Pathname.html) given an HT identifier when run on a machine
with access.


## Example

```ruby

require 'ht/pairtree'

# rootdir defaults to ENV['SDRROOTDIR'] || '/sdr1/obj'
pt = HathiTrust::Pairtree.new 

# or pass it in explicitly
rootdir = '/mypairtree/root' 
pt = HathiTrust::Pairtree.new(root: rootdir)


id = 'uc1.c3292592'

pt.path_for(id)
# => #<Pathname:/sdr1/obj/uc1/pairtree_root/c3/29/25/92/c3292592>

# Equivalent method names
pt.path_to(id)
pt.dir(id)
pt[id]

# Get the underlying Pairtree object for an id

pairtree = pt.pairtree(id)

```
## htdir command line utility
`ht-pairtree` ships with a command-line utility `htdir <id> <optional root>` give a string representation of the directory for an htid.
Potentially useful for something like

```sh
cd `htdir 'ia.ark:/13960/t9w10cs7x'`
```

I wanted to include an 'htcd' utility which would do exactly what's above, but ruby gems can't ship with shell scripts that will get
found on the path, and ruby processes can't change the working directory for the parent shell. You can 
get the same effect with

```shell
function htcd() {
  cd `htdir "$1"`
}
```


## Installation

Add this line to your application's Gemfile:

```ruby
gem 'ht-rpairtree'
```

And then execute:
```
    $ bundle
```

Or, install it yourself as:

```ruby
$ gem install 'ht-pairtree'
```

Require it as

```ruby
require 'ht/pairtree'
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/hathitrust/ht-pairtree

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT)
