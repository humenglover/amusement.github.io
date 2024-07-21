create table if not exists student.amusement_park
(
    id              int auto_increment
        primary key,
    attraction_name varchar(100) null,
    description     text         null,
    image_path      varchar(255) null
);

create index idx_attraction_name
    on student.amusement_park (attraction_name);

create table if not exists student.hot_projects
(
    id         int auto_increment
        primary key,
    image      varchar(255) null,
    name       varchar(100) null,
    excitement varchar(50)  null,
    views      int          not null
);

create table if not exists student.table_carousel
(
    url   char(255) not null,
    title char(255) not null,
    color char(255) not null
)
    comment '轮播图';

create table if not exists student.table_projects
(
    name       varchar(255)   not null
        primary key,
    adultPrice decimal(10, 2) null,
    childPrice decimal(10, 2) null
);

create table if not exists student.table_user
(
    id           int auto_increment
        primary key,
    username     varchar(10) not null comment '用户名',
    password     char(20)    not null comment '密码',
    phone_number char(11)    not null comment '手机号'
)
    comment '用户表';

create table if not exists student.comments
(
    id              int auto_increment
        primary key,
    username        varchar(10)  null,
    attraction_name varchar(100) null,
    comment_text    text         null,
    constraint comments_ibfk_1
        foreign key (username) references student.table_user (username)
);

create index username
    on student.comments (username);

create table if not exists student.table_orderform
(
    id              int auto_increment
        primary key,
    project         varchar(255)   null,
    ticket_type     varchar(255)   null,
    ticket_price    decimal(10, 2) null,
    ticket_quantity int            null,
    username        varchar(255)   null,
    constraint table_orderform_ibfk_1
        foreign key (username) references student.table_user (username)
);

create index username
    on student.table_orderform (username);

create index username
    on student.table_user (username);

create table if not exists student.table_userpage
(
    id        int auto_increment
        primary key,
    username  varchar(50)                                   null,
    gender    varchar(10)                                   null,
    birthday  date                                          null,
    signature varchar(255) default '你还没有写过任何内容哟' null,
    constraint username
        unique (username)
);

