<template>
    <div class="recent-table table-responsive">
        <table class="table">
            <thead>
                <tr>
                    <th class="f-light">Item</th>
                    <th class="f-light">Qty</th>
                    <th class="f-light">Price</th>
                    <th class="f-light">Status</th>
                    <th class="f-light">Total Price</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>
                        <div class="product-content">
                            <div class="order-image">
                                <img src="@/assets/images/dashboard-2/order/sub-product/5.png" alt="television" />
                            </div>
                            <div>
                                <h6 class="f-14 mb-0">
                                    <router-link to="/ecommerce/order/history">Sony</router-link>
                                </h6>
                                <span class="f-light f-12">Id : #CFDE-2163</span>
                            </div>
                        </div>
                    </td>
                    <td class="f-w-500">X1</td>
                    <td class="f-w-500">$56.00</td>
                    <td class="f-w-500">
                        <div class="recent-status font-danger">
                            <svg class="me-1">
                                <use href="@/assets/svg/icon-sprite.svg#24-hour"></use>
                            </svg>Rejected
                        </div>
                    </td>
                    <td class="f-w-500">$390.00</td>
                </tr>
                <tr>
                    <td>
                        <div class="product-content">
                            <div class="order-image">
                                <img src="@/assets/images/dashboard-2/order/sub-product/6.png" alt="television" />
                            </div>
                            <div>
                                <h6 class="f-14 mb-0">
                                    <router-link to="/ecommerce/order/history">Samsung</router-link>
                                </h6>
                                <span class="f-light f-12">Id : #CFDE-2780</span>
                            </div>
                        </div>
                    </td>
                    <td class="f-w-500">X2</td>
                    <td class="f-w-500">$100.00</td>
                    <td class="f-w-500">
                        <div class="recent-status font-success">
                            <svg class="me-1">
                                <use href="@/assets/svg/icon-sprite.svg#24-hour"></use>
                            </svg>Verified
                        </div>
                    </td>
                    <td class="f-w-500">$870.00</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>