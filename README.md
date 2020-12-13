# Portland Charter

Free Open-Source participatory democracy, citizen participation and open government for cities and organizations

This is the open-source repository for Portland Charter, based on [Decidim](https://github.com/decidim/decidim).

## Setup

```bash
APP_NAME="Portland Charter"
docker run -it -v "$(pwd):/code" decidim/decidim ${APP_NAME}
cd Portland\ Charter
heroku git:remote -a portlandcharter
git add .
git commit -m "Portland Charter"
git push heroku main
heroku run rake db:migrate
heroku run rails console
```

```ruby
user = Decidim::System::Admin.new(email: 'admin@portlandcharter.test', password: <password>, password_confirmation: <password>)
user.save!
```

## Setting up the application

You will need to do some steps before having the app working properly once you've deployed it:

1. Open a Rails console in the server: `bundle exec rails console`
2. Create a System Admin user:
```ruby
user = Decidim::System::Admin.new(email: <email>, password: <password>, password_confirmation: <password>)
user.save!
```
3. Visit `<your app url>/system` and login with your system admin credentials
4. Create a new organization. Check the locales you want to use for that organization, and select a default locale.
5. Set the correct default host for the organization, otherwise the app will not work properly. Note that you need to include any subdomain you might be using.
6. Fill the rest of the form and submit it.

You're good to go!
