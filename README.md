# Tupper

Tupper is a helper for processing uploaded file via web form.

## Installation

Add this line to your application's Gemfile:

    gem 'tupper'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install tupper

## Usage

usage on Sinatra application:

### upload

```ruby
post '/upload' do
  tupper = Tupper.new session
  tupper.upload params[:file_from_form]
  redirect '/somewher', 302
end
```
### process uploaded file

```ruby
get '/show_file_info' do
  tupper = Tupper.new session
  if tupper.has_uploaded_file?
    filename = tupper.uploaded_file
    # do something
  end
  erb :show_file_info, locals: { tupper: tupper }
end
```

### cleanup uploaded file and session
```ruby
post '/cleanup' do
  tupper = Tupper.new session
  tupper.cleanup
  redirect '/', 302
end
```

### more info

see /sample

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
