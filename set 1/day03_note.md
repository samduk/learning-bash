`NUMBER=$((RANDOM%10+1))`

`+1` helps us to get to 10, without `+1`, the answer will be anything between 0-9

`function determine_operation(){
  RAND=$((RANDOM%3))
  case $RAND in
    1) OPERATION='*';;
    2) OPERATION='+';;
    3) OPERATION='-';;
  esac
}`

`function calculate_answer(){
  CORRECT_ANSWER="$(echo "$QUESTION" | bc)"
}`

`function check_answer(){
  if [ $ANSWER -eq $CORRECT_ANSWER 2>/dev/null ]; then
    echo "Correct!"
    CORRECT=1
    if [ $TRY -ne 1]; then
      write_log
  fi
}`


`while true
do
  CORRECT=0
  TRY=1

  generate_question
  calculate_answer

  echo "How much is $QUESTION ? (attempt $TRY)"
  echo "(Correct answer is $CORRECT_ANSWER)"
  while [ $CORRECT -ne 1 ] && [ $TRY -le $MAX_TRIES ]
  do
    read ANSWER
    check_answer
  done`
done
