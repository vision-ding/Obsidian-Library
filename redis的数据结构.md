1.字符串
redisClient有一个成员c->db,类型是redisDb
db有一个成员是dict，类型是dict
db->dict是key-value格式，其中key永远是string类型，value可以是string类型，可以是hash类型，可以是list类型, 也可以是set类型
因此，所有的数据都存储在c->db->dict当中。


