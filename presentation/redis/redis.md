!SLIDE commandline incremental code
	$ heroku addons:add redistogo:nano
	Adding redistogo:nano to freezing-autumn-489... done, v14 (free)
	
* uses http://redistogo.com	
* See http://devcenter.heroku.com/articles/redistogo
* Add to Gemfile: gem 'redis'
* Add config/initializers/redis.rb
	@@@ruby
	uri = URI.parse(ENV["REDISTOGO_URL"])
	REDIS = Redis.new(:host => uri.host, :port => uri.port, :password => uri.password)

!SLIDE commandline incremental

	$ heroku run console
	Running console attached to terminal... up, run.5
	Loading production environment (Rails 3.0.8)
	irb(main):001:0> REDIS
	=> #<Redis client v2.2.1 connected to redis://bass.redistogo.com:9581/0 (Redis v2.2.5)>
	irb(main):002:0> REDIS.set("a", 42)
	=> "OK"
	irb(main):003:0> REDIS.get "a"
	=> "42"

!SLIDE small
# Redis methods
:[], :[]=, :append, :auth, :bgrewriteaof, :bgsave, :blpop, :brpop, :brpoplpush, :client, :config, :dbsize, :debug, :decr, :decrby, :del, :discard, :echo, :exec, :exists, :expire, :expireat, :flushall, :flushdb, :get, :getbit, :getrange, :getset, :hdel, :hexists, :hget, :hgetall, :hincrby, :hkeys, :hlen, :hmget, :hmset, :hset, :hsetnx, :hvals, :id, :incr, :incrby, :info, :keys, :lastsave, :lindex, :linsert, :llen, :lpop, :lpush, :lpushx, :lrange, :lrem, :lset, :ltrim, :mapped_hmget, :mapped_hmset, :mapped_mget, :mapped_mset, :mapped_msetnx, :method_missing, :mget, :mon_enter, :mon_exit, :mon_synchronize, :mon_try_enter, :monitor, :move, :mset, :msetnx, :multi, :new_cond, :object, :persist, :ping, :pipelined, :psubscribe, :publish, :punsubscribe, :quit, :randomkey, :rename, :renamenx, :rpop, :rpoplpush, :rpush, :rpushx, :sadd, :save, :scard, :sdiff, :sdiffstore, :select, :set, :setbit, :setex, :setnx, :setrange, :shutdown, :sinter, :sinterstore, :sismember, :slaveof, :smembers, :smove, :sort, :spop, :srandmember, :srem, :strlen, :subscribe, :subscribed?, :substr, :sunion, :sunionstore, :sync, :try_mon_enter, :ttl, :type, :unsubscribe, :unwatch, :watch, :without_reconnect, :zadd, :zcard, :zcount, :zincrby, :zinterstore, :zrange, :zrangebyscore, :zrank, :zrem, :zremrangebyrank, :zremrangebyscore, :zrevrange, :zrevrangebyscore, :zrevrank, :zscore, :zunionstore
