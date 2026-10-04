# Chapter 11: Content Management System 297

);

```
@
# Table structure for table 'stories'
#
CREATE TABLE stories (
    story_id int(11) DEFAULT '0' NOT NULL auto_increment,
    stage_id int(11) DEFAULT '0' NOT NULL,
    publish_dt date,
    headline varchar(255),
    subtitle varchar(255),
    byline_prefix varchar(20),
    summary text,
    body text,
    PRIMARY KEY (story_id),
    KEY story_stage_key (stage_id)
);
```

```
@
# Table structure for table 'story_author_map'
#
CREATE TABLE story_author_map (
    story_id int(11) DEFAULT '0' NOT NULL,
    author_id int(11) DEFAULT '0' NOT NULL,
    PRIMARY KEY (story_id),
    KEY author_story_map_key (author_id)
);
```

```
@
# Table structure for table 'story_versions'
#
CREATE TABLE story_versions (
    story_id int(11) DEFAULT '0' NOT NULL,
    modify_dt timestamp(0),
    modify_by varchar(20) DEFAULT '' NOT NULL,
    stage_id int(11) DEFAULT '0' NOT NULL,
    publish_dt date,
    headline varchar(255),
    subtitle varchar(255),
    byline_prefix varchar(20),
    summary text,
    body text,
    KEY story_version_key (story_id,modify_dt)
);
```