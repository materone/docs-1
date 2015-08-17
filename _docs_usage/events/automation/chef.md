---
layout: page
title: Chef
---
## Description
The CoScale plugin for Chef will push events to the CoScale infrastructure every time your make a configuration chance.

## Installation
<a href="https://github.com/CoScale/coscale-chef-plugin" target="_blank" class="btn btn-large btn-info"><i class="fa fa-3x fa-fw fa-github-square"></i> Github repository</a>

1. The content of the recipes/default.rb should be added in the recipe that will create the event;
2. The parameters of the Chef::Coscale.event() function should be changed with the client parameters;
3. The file libraries/coscale.rb should be added in the cookbook libraries directory.