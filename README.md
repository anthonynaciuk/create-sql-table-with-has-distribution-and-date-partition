# create-sql-table-with-has-distribution-and-date-partition

CREATE TABLE [logdata]
(
    [Correlation id] [varchar](200) NULL,
	[Operation name] [varchar](200) NULL,
	[Status] [varchar](100) NULL,
	[Event category] [varchar](100) NULL,
	[Level] [varchar](100) NULL,
	[Time] [datetime] NULL,
	[Subscription] [varchar](200) NULL,
	[Event initiated by] [varchar](1000) NULL,
	[Resource type] [varchar](1000) NULL,
	[Resource group] [varchar](1000) NULL,
    [Resource] [varchar](2000) NULL
)
WITH  
(   
    DISTRIBUTION = HASH ([Operation name]),
    PARTITION ( [Time] RANGE RIGHT FOR VALUES
            ('2023-01-01','2023-02-01','2023-03-01','2023-04-01'))
)

-- You will see 5 partitions , one is for those values prior to 2023-01-01
![image](https://github.com/anthonynaciuk/create-sql-table-with-has-distribution-and-date-partition/assets/114329733/99cd1e5e-16df-44f1-bc65-f5d62e18951f)
