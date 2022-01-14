Usage
=====

.. _installation:

Installation
------------

To use Lumache, first install it using pip:

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']


.. code-block:: console

    MTURK_SANDBOX = 'https://mturk-requester-sandbox.us-east-1.amazonaws.com'
    mturk = boto3.client('mturk',
    aws_access_key_id = keys_id,
    aws_secret_access_key = keys,
    region_name='us-east-1',
    endpoint_url = mturk_environment['endpoint']
    )


To check account balance:


.. code-block:: console

    print ("I have $" + mturk.get_account_balance()['AvailableBalance'] + " in my Sandbox account")


Create qualifications:
----------------------

    
.. code-block:: console

    def worker_requirements_quali(live):
    
       QidDic=get_Qid()
       if live==True:
           print("in live mode!")    
           requirements_quali = [
           {
               'QualificationTypeId': QidDic["BasicQualification"],
               'Comparator': 'DoesNotExist',
           },
           {
               'QualificationTypeId': QidDic["Invitation"],
               'Comparator': 'Exists',
           },

           {
               'QualificationTypeId': '000000000000000000L0', ## acceptance rate>95%
               'Comparator': 'GreaterThanOrEqualTo',
               'IntegerValues': [95],
               'RequiredToPreview': True,
           },{
               'QualificationTypeId': '00000000000000000040', #accepted HITs>500
               'Comparator': 'GreaterThanOrEqualTo',
               'IntegerValues': [500],
               'RequiredToPreview': True,
           },
           {
               'QualificationTypeId': '00000000000000000071',# located in U.S.
               'Comparator': 'EqualTo',
               'LocaleValues': [{'Country':'US'}],
               'RequiredToPreview': True,
           }
           ]
       else:
           requirements_quali=[
           {
               'QualificationTypeId': QidDic["SandBox"],
               'Comparator': 'DoesNotExist',
           }
           ]
       return requirements_quali

