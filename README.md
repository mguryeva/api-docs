<p align="center">
  <img src="https://raw.githubusercontent.com/steemit/steemit-docs/master/source/images/steemdev.png" alt="Steemit API Portal" width="226">
  <br>
  <br>
  
</p>

<p align="center">Welcome to the <a href="https://steemit.com" target="_blank">steemit</a> API and Developer Docs.</p>

<p align="center"><img src="https://raw.githubusercontent.com/steemit/steemit-docs/master/source/images/preview.png" width=700 alt="\"></p>

<p align="center">The Live Steem API Developer docs can be viewed at<a href="https://steemit.github.io/steemit-docs" target="_blank"> steemit API docs</a></p>

------------------------------

Steemit is the social media platform where everyone gets paid for creating and curating content.

The following API documents provide details on how to interact with the Steem blockchain database API which can get information on accounts, content, blocks and much more!

The developer portal will also serve as a toolbox for steem clients, libraries, and language wrappers.

### Installing Locally
------------------------------

Steemit docs are built with the great [slate](https://github.com/lord/slate) framework.  Slate supports markdown for editing our API documentation. 

1. Clone this repository to your hard drive with `git clone https://github.com/steemit/steemit-docs.git`
2. `cd steemit-docs`
3. Initialize and start Slate. You can either do this locally, or with Vagrant:

```shell
# either run this to run locally
bundle install
bundle exec middleman server

# OR run this to run with vagrant
vagrant up
```

4. The docs should now be viewable at `http://localhost:4567/`

### Contributing and Publishing New Updates
------------------------------

1.  Commit your changes locally
2.  Make sure your origin remote is set to `https://github.com/steemit/steemit-docs`
3.  Git push origin master
4.  Run ./deploy.sh