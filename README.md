# great_expectations
## Проверки таблицы bektova.ods_payment
Минимальное количество записей (проверить наличие данных)
###### batch.expect_table_row_count_to_be_between(min_value=900)
Количество колонок (проверка структуры таблицы)
###### batch.expect_table_column_count_to_equal(value=8)
Состав и порядок полей (проверка структуры таблицы)
###### batch.expect_table_columns_to_match_ordered_list(column_list=['user_id', 'pay_doc_type', 'pay_doc_num', 'account', 'phone', 'billing_period', 'pay_date', 'sum'])
Уникальность записей по сочетанию ключевых полей (отсутствие дублирования)
###### batch.expect_compound_columns_to_be_unique(column_list=['user_id', 'pay_doc_num', 'pay_date'])

## Проверка для конкретных полей
### `user_id`
отсутствие нулевых значений (целостность)
###### batch.expect_column_values_to_not_be_null(column='user_id')
проверка типов данных (формат)
###### batch.expect_column_values_to_be_in_type_list(column='user_id', type_list=['INTEGER', 'BIGINT'])
### `pay_doc_type`
отсутствие нулевых значений (целостность)
###### batch.expect_column_values_to_not_be_null(column='pay_doc_type')
проверка корректности наименований платежных систем
###### batch.expect_column_distinct_values_to_equal_set(column='pay_doc_type', value_set=['MASTER', 'MIR', 'VISA'])
проверка равномерности распределения по платежным системам через расхождение Кульбака-Лейблера (относительная энтропия указанного столбца по отношению к объекту раздела будет ниже заданного порогового значения)
###### batch.expect_column_kl_divergence_to_be_less_than(column='pay_doc_type', partition_object={'values': ['MASTER', 'MIR', 'VISA'], 'weights': [0.335, 0.35, 0.315]}, threshold=0.6)
### `pay_doc_num`
отсутствие нулевых значений (целостность)
###### batch.expect_column_values_to_not_be_null(column='pay_doc_num')
### `account`
отсутствие нулевых значений (целостность)
###### batch.expect_column_values_to_not_be_null(column='account')
минимальная длина поля
###### batch.expect_column_value_lengths_to_be_between(column='account', min_value=1)
### `pay_date`
отсутствие нулевых значений (целостность)
###### batch.expect_column_values_to_not_be_null(column='pay_date')
проверка корректности даты платежа на минимальное и максимальное значение
###### batch.expect_column_values_to_be_between(column='pay_date', max_value='2021-05-12 22:11:35.722715', min_value='2012-01-04 00:00:00', parse_strings_as_datetimes=True)
### `sum`
отсутствие нулевых значений (целостность)
###### batch.expect_column_values_to_not_be_null(column='sum')
отсутствие экстремальных значений
###### batch.expect_column_values_to_be_between(column='sum', max_value=99999, min_value=0.01)
проверка типов данных (формат)
###### batch.expect_column_values_to_be_in_type_list(column='sum', type_list=['NUMERIC'])
или так
###### batch.expect_column_values_to_be_of_type(column='sum', type_='NUMERIC')
