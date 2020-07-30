<template>
	<div>
		<section class="women-banner spad">
			<div class="container-fluid">
				<div class="row">
					<div class="col-lg-12 mt-5" v-if="products.length > 0">
						<carousel class="product-slider" :items="3" :nav="false" :autoplay="tre" :dots="false">
							<div class="product-item" v-for="itemProduct in products" :key="itemProduct.id">
								<div class="pi-pic">
									<img :src="itemProduct.galleries[0].photo" alt="img" />
									<ul>
										<li class="w-icon active" @click="saveKeranjang(itemProduct.id , itemProduct.name , itemProduct.price , itemProduct.galleries[0].photo)">
											<!-- <router-link to="/cart"> -->
												<a href="#" ><i class="icon_bag_alt"></i></a>
											<!-- </router-link> -->
										</li>
										<li class="quick-view">
											<router-link :to="'/product/'+itemProduct.id">
												+ Quick View
											</router-link>
										</li>
									</ul>
								</div>
								<div class="pi-text">
									<div class="catagory-name">{{itemProduct.type}}</div>
									<router-link to="/product">
										<h5>{{itemProduct.name}}</h5>
									</router-link>
									<div class="product-price">
										{{itemProduct.price}}
										<span>$35.00</span>
									</div>
								</div>
							</div>	
						</carousel>
					</div>
					<div class="col-lg-12" v-else>
						<p>Produk tidak tersedia</p>
					</div>
				</div>
			</div>
		</section>
	</div>
</template>

<script>
import carousel from 'vue-owl-carousel'
import axios from 'axios';


export default {
	name: 'WomenStyle',
	components: {
		carousel
	},
	data() {
		return {
			products: [],
			keranjangUser:[]
		}
	},
	methods: {
		saveKeranjang(idProduct, nameProduct, priceProduct, photoProduct) {

			let productStored = {
				'id': idProduct,
				'name': nameProduct,
				'price': priceProduct,
				'photo': photoProduct
			}

			this.keranjangUser.push(productStored);
			const parsed = JSON.stringify(this.keranjangUser);
			localStorage.setItem('keranjangUser', parsed);
		}
	},
	mounted() {
		axios
			.get("http://shayna-backend.belajarkoding.com/api/products")
			.then(res => (this.products = res.data.data.data))
			.catch(err => console.log(err));

	},
}
</script>

<style scoped>
.product-item {
	margin-right: 25px;
}
</style>