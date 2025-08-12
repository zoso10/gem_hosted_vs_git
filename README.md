# gem_hosted_vs_git

This project has two Gemfiles. One points to rubygems and bundles gems the "normal" way. The other, points to gems via their GitHub URL and bundles via git. The goal of this repository is to experiment and compare the `bundle install` runtimes of each.

## Running

There are two bash scripts in the repository: `test_git` and `test_hosted`. They both function the same way:

1. Uninstall all existing gems (to ensure a stable test environment)
1. Install bundler v2.7.1
1. Run `bundle install` for the specific gemfile
1. Print the runtime
1. Repeat 10 times
1. Print the averagae runtime

**Warning**: Running the scripts will nuke all your gems for ruby version 3.4.5!

## Results

| Gems Bundled | Hosted Time | Git Time |
| ------------ | ----------- | -------- |
| 1 gem        | 0.5261 sec  | 0.6658 sec |
| 10 gems      | 3.7265 sec  | 6.7824 sec |
| 10 gems, rails | 4.8485 sec  | 9.1165 sec |
| 15 gems      | 5.1074 sec | 11.3457 sec
| 15 gems, rails | 5.0287 sec | 11.0934 sec |
| 14 gems, rails, aws-sdk | 4.9466 sec | 12.1143 sec |
