# Twitter Stuff

```postgresql
CREATE TABLE location (
    latitude double precision,
    longitude double precision,
    country text,
    place text,
    PRIMARY KEY(latitude, longitude)
);
```

## Composite key

The FOREIGN KEY in tweets table for location table PRIMARY KEY is composed of two table values latitude and longitude.

```postgresql
CREATE TABLE tweets (
    id bigint,
    date date,
    hour time,
    uname text,
    FOREIGN KEY (uname) REFERENCES users (uname),
    message text,
    favs bigint,
    rts bigint,
    latitude double precision,
    longitude double precision,
    FOREIGN KEY (latitude, longitude) REFERENCES location (latitude, longitude),
    picture text,
    listed bigint,
    lang text,
    url text,
    PRIMARY KEY(id)
);
```

```postgresql
CREATE TABLE users (
    uname text,
    nickname text,
    bio text,
    followers bigint,
    following bigint,
    PRIMARY KEY(uname)
);
```
