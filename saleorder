url = 'http://localhost:8069' #<insert server URL>
db = 'testdb' #<insert database name>
username = 'admin'
password = 'admin' #<insert password for your admin user (default: admin)>

import xmlrpclib
from datetime import datetime


common = xmlrpclib.ServerProxy('{}/xmlrpc/2/common'.format(url))
uid = common.authenticate(db, username, password, {})
print("Logged In User ID",uid)
models = xmlrpclib.ServerProxy('{}/xmlrpc/2/object'.format(url))


class Order():
	# Create order
	def create(self):
		model_name = "sale.order"
		line_vals = {
				'product_id': 1047,  #product id 
				'name': "product description", #product description
				'product_uom_qty': 1, #Qty
				'price_unit': 100,  #sale price
			}
		order_vals = {
				'partner_id': 5503,				
				'validity_date': '2020-01-10',
				'order_line': [(0, 0, line_vals)],
			}
		new_id = models.execute_kw(db, uid, password, model_name, 'create', [order_vals])
		return new_id		 
	

order = Order()
print("New Order ID: ",order.create())
