### Regular Expression Examples

```bash
dev@dev: cat TEST
apple
pear
orange 
pineapple
watermelon
banana
car

## Dot, where \b set the boundary of word matches three characters exactly
dev@dev: grep '\b.a.\b' TEST
car

## Anchors 
dev@dev: grep '^apple' TEST
apple

dev@dev: grep 'apple$' TEST ## find word apple where it occurs at the end of the line
apple
pineapple 

## Bracket Expressions
dev@dev: grep '[abc]a' TEST
banana
car

dev@dev: grep '[^abc]a' TEST ## negation, first character in bracket expression is ^
pear
orange 
pineapple
watermelon
banana

## Character Classes
dev@dev: grep '^[[:upper:]]*$' TEST ## find string with all uppercase
PEACH
LEMON

## Quantifiers
dev@dev: grep -E '\b[a-z]{3}\b' TEST ## -E enables extended regular expression, allows the use of quantifiers 
car

```