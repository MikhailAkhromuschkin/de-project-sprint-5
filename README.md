# Проект "спринт 5"

<p>Нам необходимо построить витрину, содержащую информацию о выплатах курьерам.</p>

### Состав витрины:
</br>
+ id — идентификатор записи.  </br>
+ courier_id — ID курьера, которому перечисляем.  </br>
+ courier_name — Ф. И. О. курьера.  </br>
+ settlement_year — год отчёта.  
+ settlement_month — месяц отчёта, где 1 — январь и 12 — декабрь.  </br>
+ orders_count — количество заказов за период (месяц).  </br>
+ orders_total_sum — общая стоимость заказов.  </br>
+ rate_avg — средний рейтинг курьера по оценкам пользователей.  </br>
+ order_processing_fee — сумма, удержанная компанией за обработку заказов, которая высчитывается как orders_total_sum * 0.25.  </br>
+ courier_order_sum — сумма, которую необходимо перечислить курьеру за доставленные им/ей заказы. За каждый доставленный заказ курьер должен получить некоторую сумму в зависимости от рейтинга (см. ниже).  </br>
+ courier_tips_sum — сумма, которую пользователи оставили курьеру в качестве чаевых.  </br>
+ courier_reward_sum — сумма, которую необходимо перечислить курьеру. Вычисляется как courier_order_sum + courier_tips_sum * 0.95 (5% — комиссия за обработку платежа).  </br>

<p>Правила расчёта процента выплаты курьеру в зависимости от рейтинга, где r — это средний рейтинг курьера в расчётном месяце:</p></br>

+ r < 4 — 5% от заказа, но не менее 100 р.;
+ 4 <= r < 4.5 — 7% от заказа, но не менее 150 р.;
+ 4.5 <= r < 4.9 — 8% от заказа, но не менее 175 р.;
+ 4.9 <= r — 10% от заказа, но не менее 200 р.  


<p>Данные о заказах уже есть в хранилище. Данные курьерской службы вам необходимо забрать из API курьерской службы, после чего совместить их с данными подсистемы заказов.</p></br>

<p>Отчёт собирается по дате заказа. Если заказ был сделан ночью и даты заказа и доставки не совпадают, в отчёте стоит ориентироваться на дату заказа, а не дату доставки. Иногда заказы, сделанные ночью до 23:59, доставляют на следующий день: дата заказа и доставки не совпадёт. Это важно, потому что такие случаи могут выпадать в том числе и на последний день месяца. Тогда начисление курьеру относите к дате заказа, а не доставки.</p>
