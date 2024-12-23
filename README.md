!/bin/bash
if [ "$1" == "--help" ] || [ "$1" == "-h" ]; then
    echo "Формат вызова: topsize [--help] [-h] [-N] [-s minsize] [--] [dir...]"
    exit 0
fi
N=9999999
minsize=1
human_readable=0
directories=()
while [ "$1" != "" ]; do
    case $1 in
        -N) shift
            N=$1
            ;;
        -s) shift
            minsize=$1
            ;;
        -h) human_readable=1
            ;;
        --) shift
                    break
            ;;
        *) directories+=("$1")
            ;;
    esac
    shift
done 
if [ ${#directories[@]} -eq 0 ]; then
    directories+=(".")
fi
for dir in "${directories[@]}"; do
    find "$dir" -type f -size +${minsize}c -exec stat -c "%s %n" {} \; | sort>
        if [ $human_readable -eq 1 ]; then
            size=$(du -h "$name" | awk '{print $1}')
        fi
        echo "$size $name"
    done
done
