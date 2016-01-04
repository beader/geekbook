# Data Wrangling

### 1. `data.table`

[data.table cheat sheet](https://s3.amazonaws.com/assets.datacamp.com/img/blog/data+table+cheat+sheet.pdf)

### 2. reshape data using `data.table`

Reference: [Efficient reshaping using data.tables](https://rawgit.com/wiki/Rdatatable/data.table/vignettes/datatable-reshape.html)

```r
DT
#    family_id age_mother dob_child1 dob_child2 dob_child3
# 1:         1         30 1998-11-26 2000-01-29         NA
# 2:         2         27 1996-06-22         NA         NA
# 3:         3         26 2002-07-11 2004-04-05 2007-09-02
# 4:         4         32 2004-10-10 2009-08-27 2012-07-21
# 5:         5         29 2000-12-05 2005-02-28         NA
```

#### a. `melt` data.tables (wide to long)

```r
DT.m1 = melt(DT, measure.vars = c("dob_child1", "dob_child2", "dob_child3"), 
               variable.name = "child", value.name = "dob")
DT.m1
#     family_id age_mother      child        dob
#  1:         1         30 dob_child1 1998-11-26
#  2:         2         27 dob_child1 1996-06-22
#  3:         3         26 dob_child1 2002-07-11
#  4:         4         32 dob_child1 2004-10-10
#  5:         5         29 dob_child1 2000-12-05
#  6:         1         30 dob_child2 2000-01-29
#  7:         2         27 dob_child2         NA
#  8:         3         26 dob_child2 2004-04-05
#  9:         4         32 dob_child2 2009-08-27
# 10:         5         29 dob_child2 2005-02-28
# 11:         1         30 dob_child3         NA
# 12:         2         27 dob_child3         NA
# 13:         3         26 dob_child3 2007-09-02
# 14:         4         32 dob_child3 2012-07-21
# 15:         5         29 dob_child3         NA
```

#### b. `cast` data.tables (long to wide)

```r
dcast(DT.m1, family_id + age_mother ~ child, value.var = "dob")
#    family_id age_mother dob_child1 dob_child2 dob_child3
# 1:         1         30 1998-11-26 2000-01-29         NA
# 2:         2         27 1996-06-22         NA         NA
# 3:         3         26 2002-07-11 2004-04-05 2007-09-02
# 4:         4         32 2004-10-10 2009-08-27 2012-07-21
# 5:         5         29 2000-12-05 2005-02-28         NA
```