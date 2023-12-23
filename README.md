# Project docs

## adding new book

```code
  // Insert author
    db.run('INSERT INTO authors (name) VALUES (?)', [authorName], function (err) {
        if (err) {
            console.error(err);
            res.status(500).json({ error: 'Error inserting author.' });
        } else {
            const authorId = this.lastID;

            // Insert book
            db.run('INSERT INTO books (title, year, author_id) VALUES (?, ?, ?)', [title, year, authorId], function (err) {
                if (err) {
                    console.error(err);
                    res.status(500).json({ error: 'Error inserting book.' });
                } else {
                    res.json({ success:"book added succesfully", bookId: this.lastID });
                }
            });
        }
    });
});
```


### RelationShip Diagram
![image](https://github.com/abdomagdy0/db2/assets/91535529/0d0184c0-01d1-46f4-adc2-8d337d19ade8)
