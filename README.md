# PyschoPy

# Under the "Begin Experiment" Tab, copy and paste the following:

inputText = ""

# Under the "Begin Routine" Tab, copy and paste the following:

theseKeys=""
shift_flag = False
time_limit = True
text_3.alignHoriz ='left'

# Under the "Each Frame" Tab, copy and paste the following:

n= len(theseKeys)

i = 0

while i < n:

    if theseKeys[i] == 'return':
        # pressing RETURN means time to stop
        continueRoutine = False
        break

    elif theseKeys[i] == 'backspace':
        inputText = inputText[:-1]  # lose the final character
        i = i + 1

    elif theseKeys[i] == 'space':
        inputText += ' '
        i = i + 1

    elif theseKeys[i] in ['lshift', 'rshift']:
        shift_flag = True
        i = i + 1

    else:
        if len(theseKeys[i]) == 1:
            # we only have 1 char so should be a normal key, 
            # otherwise it might be 'ctrl' or similar so ignore it
            if shift_flag:
                inputText += chr( ord(theseKeys[i]) - ord(' '))
                shift_flag = False
            else:
                inputText += theseKeys[i]

        i = i + 1
        
# Under the "Each Frame" Tab, copy and paste the following:
# This stores the final text tring in the results

thisExp.addData('inputText', inputText) 
inputText="" 


