:original_name: modelarts_05_3173.html

.. _modelarts_05_3173:

How Do I Use Multiple Ascend Cards for Debugging in a Notebook Instance?
========================================================================

An Ascend multi-card training job runs in multi-process, multi-card mode. The number of cards is equal to the number of Python processes. The Ascend underlayer reads the environment variable **RANK_TABLE_FILE**, which has been configured in the development environment, without requiring manual configuration. For example, to run a job on eight cards, the code is as follows:

.. code-block:: text

    export RANK_SIZE=8
    current_exec_path=$(pwd)
    echo 'start training'
    for((i=0;i<=$RANK_SIZE-1;i++));
    do
    echo 'start rank '$i
    mkdir ${current_exec_path}/device$i
    cd ${current_exec_path}/device$i
    echo $i
    export RANK_ID=$i
    dev=`expr $i + 0`
    echo $dev
    export DEVICE_ID=$dev
    python train.py > train.log 2>&1 &
    done

Set the environment variable **DEVICE_ID** in **train.py**.

.. code-block:: text

   devid = int(os.getenv('DEVICE_ID'))
    context.set_context(mode=context.GRAPH_MODE, device_target="Ascend", device_id=devid)
